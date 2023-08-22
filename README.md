# Energy
•	El algoritmo implementado para la gráfica del TAM

class Tam2(tk.Tk):
    def __init__(self, tmf2):
            super().__init__()

            def graficar2():
                Cmat1 = float(enter_1.get()) * 1
                Mmat1 = float(enter_2.get()) * 1
                Tmat01 = float(enter_3.get()) * 1
                Amat1 = float(enter_4.get()) * 1
                #kmat1 = float(enter_6.get()) * 1
                amat1 = float(enter_7.get()) * 1
                abp1 = ab * amat1 * tg
                Beta1 = (h1T * hgo * Amat1 * th) / (Mmat1 * Cmat1 * (h1T + hgo))

                tb = 25
                ta = Te
                hcbe = 4 * v + 5.60

                hours = []

                for i in range(0, 13):
                    IG=(2*w/Tos)*sin((math.pi*x)/Tos + sy)**2
                    TA=a *sin(2 * math.pi * ((x - b1) / (2 * b2))) + B
                    result1 = ((Amat1 * th) / (Mmat1 * Cmat1)) * (((amat1 * tg - abp1) * IG) + (
                                (h1T / (h1T + hgo)) * (ag *IG + hgo * TA) + (hcbe * (tb - TA))))
                    resultint1 = integrate(result1 * e ** (Beta1 * x), (x, 0, i))
                    resultfdt1 = resultint1*e ** (-Beta1 * i) + Tmat01*e ** (-Beta1 * i)
                    fdt1.append(resultfdt1)
                    hours.append(i)

                # create a figure
                figure_tam = Figure(figsize=(7, 6), dpi=100)

                # create FigureCanvasTkAgg object
                figure_canvas = FigureCanvasTkAgg(figure_tam, self)

                # create the toolbar
                NavigationToolbar2Tk(figure_canvas, self)

                # create axes
                axes = figure_tam.add_subplot()

                # create the graph
                axes.plot(hours, fdt1, mfc='red', linestyle='dashed', marker='o')
                axes.set_title('Temperatura del TAM', fontdict={'fontsize': 14, 'color': 'tab:blue'})
                axes.set_ylabel('T [°C]')
                axes.set_xlabel('Horas')
                axes.grid(axis='y', color='gray', linestyle='dotted')

                division = 10 / 3
                for j in range(len(hours)):
                    axes.text(j, fdt1[j] + .25, round(fdt1[j], 3), ha='center', va='bottom', fontweight='bold',
                              size='medium', color='#000000')

                figure_canvas.get_tk_widget().pack(side=tk.TOP, fill=tk.BOTH, expand=1)

            def validate_entry(text):

                return not text.isalpha()

            tmf2.title('TAM')
            tmf2.geometry("400x240")
            lbl_t = tk.Label(tmf2, text="Ingresa el parámetro del TAM", font=('bold', 13))
            lbl_t.place(x=0, y=0)
            lbl_1 = tk.Label(tmf2, text="CTAM:", font=('bold', 10))
            lbl_1.place(x=145, y=55)
            enter_1 = tk.Entry(tmf2, width=10, validate="key", validatecommand=(tmf2.register(validate_entry), "%S"))
            enter_1.place(x=205, y=55)
            lbl_2 = tk.Label(tmf2, text="MTAM:", font=('bold', 10))
            lbl_2.place(x=145, y=75)
            enter_2 = tk.Entry(tmf2, width=10, validate="key", validatecommand=(tmf2.register(validate_entry), "%S"))
            enter_2.place(x=205, y=75)
            lbl_3 = tk.Label(tmf2, text="T0_TAM:", font=('bold', 10))
            lbl_3.place(x=145, y=115)
            enter_3 = tk.Entry(tmf2, width=10, validate="key", validatecommand=(tmf2.register(validate_entry), "%S"))
            enter_3.place(x=205, y=115)
            lbl_4 = tk.Label(tmf2, text="ATAM:", font=('bold', 10))
            lbl_4.place(x=145, y=95)
            enter_4 = tk.Entry(tmf2, width=10, validate="key", validatecommand=(tmf2.register(validate_entry), "%S"))
            enter_4.place(x=205, y=95)
            lbl_7 = tk.Label(tmf2, text="AlfaTAM:", font=('bold', 10))
            lbl_7.place(x=145, y=135)
            enter_7 = tk.Entry(tmf2, width=10, validate="key", validatecommand=(tmf2.register(validate_entry), "%S"))
            enter_7.place(x=205, y=135)

            button2 = tk.Button(tmf2, text="Salir", command=tmf2.destroy)
            button2.grid()
            button2.place(x=220, y=200)
            button3 = tk.Button(tmf2, text="Graficar", command=graficar2)
            button3.grid()
            button3.place(x=160, y=200)


•	El código del Menú

class MenuP(tk.Tk):
    def __init__(self, menu1):
        super().__init__()

        menu1.title('Menu Principal')
        menu1.geometry("420x220")



        lbl_t = tk.Label(menu1, text="Bienvenido al Calculador Térmico de Materiales", font=('bold', 14))
        lbl_t.place(x=5, y=0)
        button1 = tk.Button(menu1, text="Temperatura ambiente", width=30, command=Temp)
        button1.grid()
        button1.place(x=95, y=35)
        button2 = tk.Button(menu1, text="Irradiancia térmica", width=30, command=ThermalI)
        button2.grid()
        button2.place(x=95, y=65)
        button3 = tk.Button(menu1, text="Temperatura del material (TAM)", width=30, command=otam2)
        button3.place(x=95, y=95)
        button4 = tk.Button(menu1, text="Comparación de las gráficas", width=30, command=otam)
        button4.place(x=95, y=125)
        button5 = tk.Button(menu1, text="Salir", command=menu1.quit)
        button5.grid()
        button5.place(x=185, y=175)



def otam():

   Tam(tk.Tk())

def otam2():

    Tam2(tk.Tk())



