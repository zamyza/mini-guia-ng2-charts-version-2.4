Comando de instalacion:
````
npm install chart.js ng2-charts@2.4.3

`````

opcionalmente la version mas estable de chart.js es la 2.9.4

Luego, importa `ChartsModule` en el modulo que llama al modulo que vas a utilizar

```typescript
import { ChartsModule } from 'ng2-charts';

@NgModule({
  imports: [
    ChartsModule
  ]
})
```

## Gráfico de Torta

### Paso 1: HTML

```html
  <canvas baseChart
          [data]="datosTorta"
          [labels]="etiquetas"
          [chartType]="tipoGrafico">
  </canvas>
```

### Paso 2: TypeScript

En el archivo `component.ts`, define los datos y las opciones del gráfico dejando como **tipo de grafico 'pie'** en el html el [data] recibe un array con los datos necesarios que tiene que tener la misma cantidad de datos que el [labels] pues esta propiedad decide por orden la etiqueta de cada dato

```typescript

  public etiquetas: string[] = ['Ventas online', 'Ventas presencial', 'Ventas3'];
  public datosTorta: number[] = [300, 500, 100];
  public tipoGrafico: ChartType = 'pie';

```

## Gráfico de Barra

### Paso 1: HTML

Agrega el elemento `canvas` de `ng2-charts`:

```html
  <canvas baseChart
          [datasets]="datosBarra"
          [labels]="etiquetas"
          [options]="configuracion"
          [chartType]="tipoGrafico">
  </canvas>
```

### Paso 3: TypeScript

En el archivo `component.ts`, define los datos y las opciones del gráfico, el [datasets] recibe un array de objetos con el atributo **data** que es un array de valores y el atributo **label** que seria el titulo de esos valores

A continuacion mestro un ejemplo completo:

```typescript
  public configuracion: any = {
    responsive: true,
    scales: {
      yAxes: [
        {
          ticks: {
            min: 0, // valor minimo dentro del axis y
            max: 100 // valor maximo dentro del axis y
          }
        }
      ]
    }

  };
  public etiquetas: string[] = ['2006', '2007', '2008', '2009', '2010', '2011', '2012'];
  public tipoGrafico: ChartType = 'bar';
  public datosBarra: any[] = [
    { data: [65, 59, 80, 81, 56, 55, 40], label: 'Serie A' }
  ];
  //para un grafico de barra doble serian los datos asi
  ///public datosBarra: any[] = [
  ///  { data: [65, 59, 80, 81, 56, 55, 40], label: 'Serie A' },
  ///  { data: [28, 48, 40, 19, 86, 27, 90], label: 'Serie B' },
  ///];
```

# Colores
### html
Para setear colores en los 2 graficos en el html se le debe agregar el [colors]
```html
<canvas baseChart
          [datasets]="datosBarra"
          [labels]="etiquetas"
          [options]="configuracion"
          [chartType]="tipoGrafico"
          [colors]="colores">
</canvas>
```

### Typescript

colores debe ser un array de objetos y que por **cada objeto modifica una serie de los datos** esto quiere decir que sigue en orden la cantidad de objetos en la variable de datos, los datos a los que no se le indique color tomaran uno por defecto que es un gris

```typescript
public colores: Array<any> = [{
    backgroundColor: ['#FF6384', '#36A2EB', '#FFCE56', '#FFCE56', '#FFCE56'],
    borderColor: ['#FF6384', '#36A2EB', '#FFCE56'],
  },
  {
    backgroundColor: ['#FF6384', '#36A2EB', '#FFCE56', '#FFCE56', '#FFCE56'],
    borderColor: ['#FF6384', '#36A2EB', '#FFCE56'],
  }
  ];
```
