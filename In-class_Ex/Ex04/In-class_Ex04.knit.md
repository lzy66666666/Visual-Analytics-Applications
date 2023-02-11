---
title: "In-class Exercise 04"
author: "Li Ziyi"
date: "4 February 2023"
date-modified: "2023-02-11"
execute:
  echo: true
  eval: true
  warning: false
format: html
editor: visual
---

::: {.cell}

```{.r .cell-code}
pacman::p_load(plotly,
               DT, 
               patchwork,
               tidyverse,
               ggstatsplot,
               readxl,
               performance,
               parameters,
               see,
               gtsummary)
```
:::

::: {.cell}

```{.r .cell-code}
exam_data <- read_csv("Data/Exam_data.csv")
```
:::


# Creating an interactive scatter plot using ggplotly() method


::: {.cell}

```{.r .cell-code}
plot_ly(data = exam_data,
        x = ~MATHS,
        y = ~ENGLISH,
        color = ~RACE)
```

::: {.cell-output-display}
```{=html}
<div class="plotly html-widget html-fill-item-overflow-hidden html-fill-item" id="htmlwidget-06762a5ff1c668a0dad2" style="width:100%;height:464px;"></div>
<script type="application/json" data-for="htmlwidget-06762a5ff1c668a0dad2">{"x":{"visdat":{"64905815252e":["function () ","plotlyVisDat"]},"cur_data":"64905815252e","attrs":{"64905815252e":{"x":{},"y":{},"color":{},"alpha_stroke":1,"sizes":[10,100],"spans":[1,20]}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"xaxis":{"domain":[0,1],"automargin":true,"title":"MATHS"},"yaxis":{"domain":[0,1],"automargin":true,"title":"ENGLISH"},"hovermode":"closest","showlegend":true},"source":"A","config":{"modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false},"data":[{"x":[16,77,21,39,23,36,49,30,71,50,55,56,41,44,74,71,55,90,77,51,65,78,54,38,52,56,74,67,47,69,72,75,85,79,62,88,52,85,58,74,64,84,74,71,70,46,66,64,36,90,80,68,78,81,71,72,63,80,63,73,86,95,80,81,74,87,79,83,60,67,62,90,82,82,75,89,77,74,63,91,83,60,71,96,79,74,91,65,85,74,73,69,79,81,72,77,74,79,83,77,82,88,75,78,86,87,82,59,60,84,83,85,58,68,70,91,88,89,67,82,80,71,88,79,85,69,93,79,91,85,80,74,89,78,80,75,86,78,77,94,90,91,86,82,86,92,86,89,88,89,97,76,79,85,78,74,78,86,93,87,89,97,80,76,91,91,85,97,83,98,91,92,86,86,85,86,90,95,91,91,91,95,90,91,89,97,93,97,85,95,93,97,99],"y":[26,27,31,34,36,36,37,38,41,45,46,48,48,49,51,52,52,53,53,53,54,54,54,54,54,55,57,57,57,58,60,60,61,61,61,61,61,62,62,62,63,63,63,63,63,63,64,64,64,65,65,65,65,65,66,66,66,66,66,67,67,67,67,67,67,68,68,68,68,69,69,70,71,71,71,71,71,71,71,72,72,72,72,72,72,72,73,73,73,73,73,73,73,73,73,73,73,73,73,73,73,74,74,74,74,74,74,74,74,75,75,75,75,75,75,76,76,76,76,76,76,76,76,77,77,77,77,77,77,77,77,77,77,77,77,78,78,78,79,79,79,79,79,79,79,79,79,80,80,80,80,80,81,81,81,81,82,82,83,83,83,83,83,83,84,84,84,84,84,85,85,85,85,85,85,85,86,86,86,86,86,87,87,88,88,89,90,90,90,91,93,93,96],"type":"scatter","mode":"markers","name":"Chinese","marker":{"color":"rgba(102,194,165,1)","line":{"color":"rgba(102,194,165,1)"}},"textfont":{"color":"rgba(102,194,165,1)"},"error_y":{"color":"rgba(102,194,165,1)"},"error_x":{"color":"rgba(102,194,165,1)"},"line":{"color":"rgba(102,194,165,1)"},"xaxis":"x","yaxis":"y","frame":null},{"x":[49,35,25,42,48,40,68,78,83,78,90,92],"y":[34,43,43,52,54,58,60,64,73,78,83,87],"type":"scatter","mode":"markers","name":"Indian","marker":{"color":"rgba(252,141,98,1)","line":{"color":"rgba(252,141,98,1)"}},"textfont":{"color":"rgba(252,141,98,1)"},"error_y":{"color":"rgba(252,141,98,1)"},"error_x":{"color":"rgba(252,141,98,1)"},"line":{"color":"rgba(252,141,98,1)"},"xaxis":"x","yaxis":"y","frame":null},{"x":[9,22,11,16,18,19,35,21,24,54,36,40,20,32,32,37,30,24,19,32,31,30,41,34,35,56,58,58,25,59,33,43,52,37,44,52,63,75,49,50,78,64,47,58,74,43,62,63,58,58,45,79,50,66,65,69,54,79,65,49,76,61,64,70,64,72,68,53,63,74,69,61,75,44,66,70,84,63,65,79,52,66,85,75,76,75,81,54,77,85,83,95,83,71,73,79,79,56,87,82,81,87,80,81,90,74,87,87],"y":[21,24,27,31,31,33,36,39,39,40,40,40,40,41,42,42,43,44,44,45,46,49,49,49,50,50,50,52,53,54,54,55,56,56,56,56,57,57,57,57,58,58,58,59,59,60,61,61,61,62,62,62,63,64,64,64,64,65,65,65,66,66,66,66,66,67,67,67,68,68,68,68,69,69,70,70,70,70,71,71,72,73,73,73,75,76,77,77,77,78,78,78,78,78,79,79,80,80,81,81,82,82,82,83,84,85,85,88],"type":"scatter","mode":"markers","name":"Malay","marker":{"color":"rgba(141,160,203,1)","line":{"color":"rgba(141,160,203,1)"}},"textfont":{"color":"rgba(141,160,203,1)"},"error_y":{"color":"rgba(141,160,203,1)"},"error_x":{"color":"rgba(141,160,203,1)"},"line":{"color":"rgba(141,160,203,1)"},"xaxis":"x","yaxis":"y","frame":null},{"x":[51,67,70,67,70,75,61,76,90],"y":[41,63,67,68,70,71,78,81,92],"type":"scatter","mode":"markers","name":"Others","marker":{"color":"rgba(231,138,195,1)","line":{"color":"rgba(231,138,195,1)"}},"textfont":{"color":"rgba(231,138,195,1)"},"error_y":{"color":"rgba(231,138,195,1)"},"error_x":{"color":"rgba(231,138,195,1)"},"line":{"color":"rgba(231,138,195,1)"},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>
```
:::
:::

::: {.cell}

```{.r .cell-code}
p <- ggplot(data=exam_data, 
            aes(x = MATHS,
                y = ENGLISH)) +
  geom_point(dotsize = 1) +
  coord_cartesian(xlim=c(0,100),
                  ylim=c(0,100))
ggplotly(p)
```

::: {.cell-output-display}
```{=html}
<div class="plotly html-widget html-fill-item-overflow-hidden html-fill-item" id="htmlwidget-c654e3941e032babc91b" style="width:100%;height:464px;"></div>
<script type="application/json" data-for="htmlwidget-c654e3941e032babc91b">{"x":{"data":[{"x":[9,22,16,77,11,16,21,18,19,49,39,35,23,36,49,30,21,24,54,36,40,20,71,51,32,32,37,30,35,25,24,19,50,32,55,31,56,41,30,44,41,34,35,56,58,74,71,55,42,58,90,77,51,25,65,78,54,59,38,52,33,48,43,56,52,37,44,52,74,67,63,75,49,47,50,69,78,64,47,40,58,74,72,75,43,68,85,79,62,88,62,63,58,52,85,58,74,58,45,79,64,84,74,71,50,70,46,67,78,66,66,64,65,69,36,54,90,80,68,78,79,65,49,81,76,61,71,72,64,70,63,80,63,64,73,86,72,70,68,95,80,53,81,74,87,63,79,83,74,67,69,60,61,75,67,62,44,90,70,66,70,84,63,82,65,82,75,75,79,89,77,74,63,91,83,60,71,96,79,74,52,91,65,85,74,73,69,79,66,81,72,77,74,79,85,83,83,75,77,82,88,75,78,86,87,82,59,60,84,83,85,76,58,68,70,91,88,89,75,67,82,80,71,88,79,85,69,93,79,91,81,85,80,74,89,54,78,80,77,75,85,83,95,86,78,78,83,61,71,77,94,90,91,86,73,79,82,86,92,86,89,88,89,79,97,76,56,79,85,87,78,82,74,76,78,86,81,87,80,93,90,87,89,97,80,76,81,91,91,85,97,83,90,98,91,92,86,86,74,87,85,86,90,95,91,91,91,95,90,92,91,89,87,97,93,97,85,95,90,93,97,99],"y":[21,24,26,27,27,31,31,31,33,34,34,36,36,36,37,38,39,39,40,40,40,40,41,41,41,42,42,43,43,43,44,44,45,45,46,46,48,48,49,49,49,49,50,50,50,51,52,52,52,52,53,53,53,53,54,54,54,54,54,54,54,54,55,55,56,56,56,56,57,57,57,57,57,57,57,58,58,58,58,58,59,59,60,60,60,60,61,61,61,61,61,61,61,61,62,62,62,62,62,62,63,63,63,63,63,63,63,63,64,64,64,64,64,64,64,64,65,65,65,65,65,65,65,65,66,66,66,66,66,66,66,66,66,66,67,67,67,67,67,67,67,67,67,67,68,68,68,68,68,68,68,68,68,69,69,69,69,70,70,70,70,70,70,71,71,71,71,71,71,71,71,71,71,72,72,72,72,72,72,72,72,73,73,73,73,73,73,73,73,73,73,73,73,73,73,73,73,73,73,73,74,74,74,74,74,74,74,74,75,75,75,75,75,75,75,76,76,76,76,76,76,76,76,76,77,77,77,77,77,77,77,77,77,77,77,77,77,77,77,78,78,78,78,78,78,78,78,78,78,79,79,79,79,79,79,79,79,79,79,79,80,80,80,80,80,80,80,81,81,81,81,81,81,81,82,82,82,82,82,83,83,83,83,83,83,83,83,84,84,84,84,84,84,85,85,85,85,85,85,85,85,85,86,86,86,86,86,87,87,87,88,88,88,89,90,90,90,91,92,93,93,96],"text":["MATHS:  9<br />ENGLISH: 21","MATHS: 22<br />ENGLISH: 24","MATHS: 16<br />ENGLISH: 26","MATHS: 77<br />ENGLISH: 27","MATHS: 11<br />ENGLISH: 27","MATHS: 16<br />ENGLISH: 31","MATHS: 21<br />ENGLISH: 31","MATHS: 18<br />ENGLISH: 31","MATHS: 19<br />ENGLISH: 33","MATHS: 49<br />ENGLISH: 34","MATHS: 39<br />ENGLISH: 34","MATHS: 35<br />ENGLISH: 36","MATHS: 23<br />ENGLISH: 36","MATHS: 36<br />ENGLISH: 36","MATHS: 49<br />ENGLISH: 37","MATHS: 30<br />ENGLISH: 38","MATHS: 21<br />ENGLISH: 39","MATHS: 24<br />ENGLISH: 39","MATHS: 54<br />ENGLISH: 40","MATHS: 36<br />ENGLISH: 40","MATHS: 40<br />ENGLISH: 40","MATHS: 20<br />ENGLISH: 40","MATHS: 71<br />ENGLISH: 41","MATHS: 51<br />ENGLISH: 41","MATHS: 32<br />ENGLISH: 41","MATHS: 32<br />ENGLISH: 42","MATHS: 37<br />ENGLISH: 42","MATHS: 30<br />ENGLISH: 43","MATHS: 35<br />ENGLISH: 43","MATHS: 25<br />ENGLISH: 43","MATHS: 24<br />ENGLISH: 44","MATHS: 19<br />ENGLISH: 44","MATHS: 50<br />ENGLISH: 45","MATHS: 32<br />ENGLISH: 45","MATHS: 55<br />ENGLISH: 46","MATHS: 31<br />ENGLISH: 46","MATHS: 56<br />ENGLISH: 48","MATHS: 41<br />ENGLISH: 48","MATHS: 30<br />ENGLISH: 49","MATHS: 44<br />ENGLISH: 49","MATHS: 41<br />ENGLISH: 49","MATHS: 34<br />ENGLISH: 49","MATHS: 35<br />ENGLISH: 50","MATHS: 56<br />ENGLISH: 50","MATHS: 58<br />ENGLISH: 50","MATHS: 74<br />ENGLISH: 51","MATHS: 71<br />ENGLISH: 52","MATHS: 55<br />ENGLISH: 52","MATHS: 42<br />ENGLISH: 52","MATHS: 58<br />ENGLISH: 52","MATHS: 90<br />ENGLISH: 53","MATHS: 77<br />ENGLISH: 53","MATHS: 51<br />ENGLISH: 53","MATHS: 25<br />ENGLISH: 53","MATHS: 65<br />ENGLISH: 54","MATHS: 78<br />ENGLISH: 54","MATHS: 54<br />ENGLISH: 54","MATHS: 59<br />ENGLISH: 54","MATHS: 38<br />ENGLISH: 54","MATHS: 52<br />ENGLISH: 54","MATHS: 33<br />ENGLISH: 54","MATHS: 48<br />ENGLISH: 54","MATHS: 43<br />ENGLISH: 55","MATHS: 56<br />ENGLISH: 55","MATHS: 52<br />ENGLISH: 56","MATHS: 37<br />ENGLISH: 56","MATHS: 44<br />ENGLISH: 56","MATHS: 52<br />ENGLISH: 56","MATHS: 74<br />ENGLISH: 57","MATHS: 67<br />ENGLISH: 57","MATHS: 63<br />ENGLISH: 57","MATHS: 75<br />ENGLISH: 57","MATHS: 49<br />ENGLISH: 57","MATHS: 47<br />ENGLISH: 57","MATHS: 50<br />ENGLISH: 57","MATHS: 69<br />ENGLISH: 58","MATHS: 78<br />ENGLISH: 58","MATHS: 64<br />ENGLISH: 58","MATHS: 47<br />ENGLISH: 58","MATHS: 40<br />ENGLISH: 58","MATHS: 58<br />ENGLISH: 59","MATHS: 74<br />ENGLISH: 59","MATHS: 72<br />ENGLISH: 60","MATHS: 75<br />ENGLISH: 60","MATHS: 43<br />ENGLISH: 60","MATHS: 68<br />ENGLISH: 60","MATHS: 85<br />ENGLISH: 61","MATHS: 79<br />ENGLISH: 61","MATHS: 62<br />ENGLISH: 61","MATHS: 88<br />ENGLISH: 61","MATHS: 62<br />ENGLISH: 61","MATHS: 63<br />ENGLISH: 61","MATHS: 58<br />ENGLISH: 61","MATHS: 52<br />ENGLISH: 61","MATHS: 85<br />ENGLISH: 62","MATHS: 58<br />ENGLISH: 62","MATHS: 74<br />ENGLISH: 62","MATHS: 58<br />ENGLISH: 62","MATHS: 45<br />ENGLISH: 62","MATHS: 79<br />ENGLISH: 62","MATHS: 64<br />ENGLISH: 63","MATHS: 84<br />ENGLISH: 63","MATHS: 74<br />ENGLISH: 63","MATHS: 71<br />ENGLISH: 63","MATHS: 50<br />ENGLISH: 63","MATHS: 70<br />ENGLISH: 63","MATHS: 46<br />ENGLISH: 63","MATHS: 67<br />ENGLISH: 63","MATHS: 78<br />ENGLISH: 64","MATHS: 66<br />ENGLISH: 64","MATHS: 66<br />ENGLISH: 64","MATHS: 64<br />ENGLISH: 64","MATHS: 65<br />ENGLISH: 64","MATHS: 69<br />ENGLISH: 64","MATHS: 36<br />ENGLISH: 64","MATHS: 54<br />ENGLISH: 64","MATHS: 90<br />ENGLISH: 65","MATHS: 80<br />ENGLISH: 65","MATHS: 68<br />ENGLISH: 65","MATHS: 78<br />ENGLISH: 65","MATHS: 79<br />ENGLISH: 65","MATHS: 65<br />ENGLISH: 65","MATHS: 49<br />ENGLISH: 65","MATHS: 81<br />ENGLISH: 65","MATHS: 76<br />ENGLISH: 66","MATHS: 61<br />ENGLISH: 66","MATHS: 71<br />ENGLISH: 66","MATHS: 72<br />ENGLISH: 66","MATHS: 64<br />ENGLISH: 66","MATHS: 70<br />ENGLISH: 66","MATHS: 63<br />ENGLISH: 66","MATHS: 80<br />ENGLISH: 66","MATHS: 63<br />ENGLISH: 66","MATHS: 64<br />ENGLISH: 66","MATHS: 73<br />ENGLISH: 67","MATHS: 86<br />ENGLISH: 67","MATHS: 72<br />ENGLISH: 67","MATHS: 70<br />ENGLISH: 67","MATHS: 68<br />ENGLISH: 67","MATHS: 95<br />ENGLISH: 67","MATHS: 80<br />ENGLISH: 67","MATHS: 53<br />ENGLISH: 67","MATHS: 81<br />ENGLISH: 67","MATHS: 74<br />ENGLISH: 67","MATHS: 87<br />ENGLISH: 68","MATHS: 63<br />ENGLISH: 68","MATHS: 79<br />ENGLISH: 68","MATHS: 83<br />ENGLISH: 68","MATHS: 74<br />ENGLISH: 68","MATHS: 67<br />ENGLISH: 68","MATHS: 69<br />ENGLISH: 68","MATHS: 60<br />ENGLISH: 68","MATHS: 61<br />ENGLISH: 68","MATHS: 75<br />ENGLISH: 69","MATHS: 67<br />ENGLISH: 69","MATHS: 62<br />ENGLISH: 69","MATHS: 44<br />ENGLISH: 69","MATHS: 90<br />ENGLISH: 70","MATHS: 70<br />ENGLISH: 70","MATHS: 66<br />ENGLISH: 70","MATHS: 70<br />ENGLISH: 70","MATHS: 84<br />ENGLISH: 70","MATHS: 63<br />ENGLISH: 70","MATHS: 82<br />ENGLISH: 71","MATHS: 65<br />ENGLISH: 71","MATHS: 82<br />ENGLISH: 71","MATHS: 75<br />ENGLISH: 71","MATHS: 75<br />ENGLISH: 71","MATHS: 79<br />ENGLISH: 71","MATHS: 89<br />ENGLISH: 71","MATHS: 77<br />ENGLISH: 71","MATHS: 74<br />ENGLISH: 71","MATHS: 63<br />ENGLISH: 71","MATHS: 91<br />ENGLISH: 72","MATHS: 83<br />ENGLISH: 72","MATHS: 60<br />ENGLISH: 72","MATHS: 71<br />ENGLISH: 72","MATHS: 96<br />ENGLISH: 72","MATHS: 79<br />ENGLISH: 72","MATHS: 74<br />ENGLISH: 72","MATHS: 52<br />ENGLISH: 72","MATHS: 91<br />ENGLISH: 73","MATHS: 65<br />ENGLISH: 73","MATHS: 85<br />ENGLISH: 73","MATHS: 74<br />ENGLISH: 73","MATHS: 73<br />ENGLISH: 73","MATHS: 69<br />ENGLISH: 73","MATHS: 79<br />ENGLISH: 73","MATHS: 66<br />ENGLISH: 73","MATHS: 81<br />ENGLISH: 73","MATHS: 72<br />ENGLISH: 73","MATHS: 77<br />ENGLISH: 73","MATHS: 74<br />ENGLISH: 73","MATHS: 79<br />ENGLISH: 73","MATHS: 85<br />ENGLISH: 73","MATHS: 83<br />ENGLISH: 73","MATHS: 83<br />ENGLISH: 73","MATHS: 75<br />ENGLISH: 73","MATHS: 77<br />ENGLISH: 73","MATHS: 82<br />ENGLISH: 73","MATHS: 88<br />ENGLISH: 74","MATHS: 75<br />ENGLISH: 74","MATHS: 78<br />ENGLISH: 74","MATHS: 86<br />ENGLISH: 74","MATHS: 87<br />ENGLISH: 74","MATHS: 82<br />ENGLISH: 74","MATHS: 59<br />ENGLISH: 74","MATHS: 60<br />ENGLISH: 74","MATHS: 84<br />ENGLISH: 75","MATHS: 83<br />ENGLISH: 75","MATHS: 85<br />ENGLISH: 75","MATHS: 76<br />ENGLISH: 75","MATHS: 58<br />ENGLISH: 75","MATHS: 68<br />ENGLISH: 75","MATHS: 70<br />ENGLISH: 75","MATHS: 91<br />ENGLISH: 76","MATHS: 88<br />ENGLISH: 76","MATHS: 89<br />ENGLISH: 76","MATHS: 75<br />ENGLISH: 76","MATHS: 67<br />ENGLISH: 76","MATHS: 82<br />ENGLISH: 76","MATHS: 80<br />ENGLISH: 76","MATHS: 71<br />ENGLISH: 76","MATHS: 88<br />ENGLISH: 76","MATHS: 79<br />ENGLISH: 77","MATHS: 85<br />ENGLISH: 77","MATHS: 69<br />ENGLISH: 77","MATHS: 93<br />ENGLISH: 77","MATHS: 79<br />ENGLISH: 77","MATHS: 91<br />ENGLISH: 77","MATHS: 81<br />ENGLISH: 77","MATHS: 85<br />ENGLISH: 77","MATHS: 80<br />ENGLISH: 77","MATHS: 74<br />ENGLISH: 77","MATHS: 89<br />ENGLISH: 77","MATHS: 54<br />ENGLISH: 77","MATHS: 78<br />ENGLISH: 77","MATHS: 80<br />ENGLISH: 77","MATHS: 77<br />ENGLISH: 77","MATHS: 75<br />ENGLISH: 78","MATHS: 85<br />ENGLISH: 78","MATHS: 83<br />ENGLISH: 78","MATHS: 95<br />ENGLISH: 78","MATHS: 86<br />ENGLISH: 78","MATHS: 78<br />ENGLISH: 78","MATHS: 78<br />ENGLISH: 78","MATHS: 83<br />ENGLISH: 78","MATHS: 61<br />ENGLISH: 78","MATHS: 71<br />ENGLISH: 78","MATHS: 77<br />ENGLISH: 79","MATHS: 94<br />ENGLISH: 79","MATHS: 90<br />ENGLISH: 79","MATHS: 91<br />ENGLISH: 79","MATHS: 86<br />ENGLISH: 79","MATHS: 73<br />ENGLISH: 79","MATHS: 79<br />ENGLISH: 79","MATHS: 82<br />ENGLISH: 79","MATHS: 86<br />ENGLISH: 79","MATHS: 92<br />ENGLISH: 79","MATHS: 86<br />ENGLISH: 79","MATHS: 89<br />ENGLISH: 80","MATHS: 88<br />ENGLISH: 80","MATHS: 89<br />ENGLISH: 80","MATHS: 79<br />ENGLISH: 80","MATHS: 97<br />ENGLISH: 80","MATHS: 76<br />ENGLISH: 80","MATHS: 56<br />ENGLISH: 80","MATHS: 79<br />ENGLISH: 81","MATHS: 85<br />ENGLISH: 81","MATHS: 87<br />ENGLISH: 81","MATHS: 78<br />ENGLISH: 81","MATHS: 82<br />ENGLISH: 81","MATHS: 74<br />ENGLISH: 81","MATHS: 76<br />ENGLISH: 81","MATHS: 78<br />ENGLISH: 82","MATHS: 86<br />ENGLISH: 82","MATHS: 81<br />ENGLISH: 82","MATHS: 87<br />ENGLISH: 82","MATHS: 80<br />ENGLISH: 82","MATHS: 93<br />ENGLISH: 83","MATHS: 90<br />ENGLISH: 83","MATHS: 87<br />ENGLISH: 83","MATHS: 89<br />ENGLISH: 83","MATHS: 97<br />ENGLISH: 83","MATHS: 80<br />ENGLISH: 83","MATHS: 76<br />ENGLISH: 83","MATHS: 81<br />ENGLISH: 83","MATHS: 91<br />ENGLISH: 84","MATHS: 91<br />ENGLISH: 84","MATHS: 85<br />ENGLISH: 84","MATHS: 97<br />ENGLISH: 84","MATHS: 83<br />ENGLISH: 84","MATHS: 90<br />ENGLISH: 84","MATHS: 98<br />ENGLISH: 85","MATHS: 91<br />ENGLISH: 85","MATHS: 92<br />ENGLISH: 85","MATHS: 86<br />ENGLISH: 85","MATHS: 86<br />ENGLISH: 85","MATHS: 74<br />ENGLISH: 85","MATHS: 87<br />ENGLISH: 85","MATHS: 85<br />ENGLISH: 85","MATHS: 86<br />ENGLISH: 85","MATHS: 90<br />ENGLISH: 86","MATHS: 95<br />ENGLISH: 86","MATHS: 91<br />ENGLISH: 86","MATHS: 91<br />ENGLISH: 86","MATHS: 91<br />ENGLISH: 86","MATHS: 95<br />ENGLISH: 87","MATHS: 90<br />ENGLISH: 87","MATHS: 92<br />ENGLISH: 87","MATHS: 91<br />ENGLISH: 88","MATHS: 89<br />ENGLISH: 88","MATHS: 87<br />ENGLISH: 88","MATHS: 97<br />ENGLISH: 89","MATHS: 93<br />ENGLISH: 90","MATHS: 97<br />ENGLISH: 90","MATHS: 85<br />ENGLISH: 90","MATHS: 95<br />ENGLISH: 91","MATHS: 90<br />ENGLISH: 92","MATHS: 93<br />ENGLISH: 93","MATHS: 97<br />ENGLISH: 93","MATHS: 99<br />ENGLISH: 96"],"type":"scatter","mode":"markers","marker":{"autocolorscale":false,"color":"rgba(0,0,0,1)","opacity":1,"size":5.66929133858268,"symbol":"circle","line":{"width":1.88976377952756,"color":"rgba(0,0,0,1)"}},"hoveron":"points","showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","frame":null}],"layout":{"margin":{"t":26.2283105022831,"r":7.30593607305936,"b":40.1826484018265,"l":43.1050228310502},"plot_bgcolor":"rgba(235,235,235,1)","paper_bgcolor":"rgba(255,255,255,1)","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187},"xaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[-5,105],"tickmode":"array","ticktext":["0","25","50","75","100"],"tickvals":[0,25,50,75,100],"categoryorder":"array","categoryarray":["0","25","50","75","100"],"nticks":null,"ticks":"outside","tickcolor":"rgba(51,51,51,1)","ticklen":3.65296803652968,"tickwidth":0.66417600664176,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.689497716895},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(255,255,255,1)","gridwidth":0.66417600664176,"zeroline":false,"anchor":"y","title":{"text":"MATHS","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187}},"hoverformat":".2f"},"yaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[-5,105],"tickmode":"array","ticktext":["0","25","50","75","100"],"tickvals":[0,25,50,75,100],"categoryorder":"array","categoryarray":["0","25","50","75","100"],"nticks":null,"ticks":"outside","tickcolor":"rgba(51,51,51,1)","ticklen":3.65296803652968,"tickwidth":0.66417600664176,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.689497716895},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(255,255,255,1)","gridwidth":0.66417600664176,"zeroline":false,"anchor":"x","title":{"text":"ENGLISH","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187}},"hoverformat":".2f"},"shapes":[{"type":"rect","fillcolor":null,"line":{"color":null,"width":0,"linetype":[]},"yref":"paper","xref":"paper","x0":0,"x1":1,"y0":0,"y1":1}],"showlegend":false,"legend":{"bgcolor":"rgba(255,255,255,1)","bordercolor":"transparent","borderwidth":1.88976377952756,"font":{"color":"rgba(0,0,0,1)","family":"","size":11.689497716895}},"hovermode":"closest","barmode":"relative"},"config":{"doubleClick":"reset","modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false},"source":"A","attrs":{"64901d976fcb":{"x":{},"y":{},"type":"scatter"}},"cur_data":"64901d976fcb","visdat":{"64901d976fcb":["function (y) ","x"]},"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>
```
:::
:::


By using ggplotly, the plot has been enabled with interactivity. Take note that those aesthetic elements are not supported to be customised inside ggplot here.

# Visual Statistical Analysis with ggstatsplot

## Two-sample mean test using ggbetweenstats()


::: {.cell}

```{.r .cell-code}
ggbetweenstats(
  data = exam_data,
  x = GENDER, 
  y = MATHS,
  type = "p",
  messages = FALSE
)
```

::: {.cell-output-display}
![](In-class_Ex04_files/figure-html/unnamed-chunk-5-1.png){width=672}
:::
:::


## Build a visual for Significant Test of Correlation using ggscatterstats()


::: {.cell}

```{.r .cell-code}
ggscatterstats(
  data = exam_data,
  x = MATHS,
  y = ENGLISH,
  marginal = TRUE,
  )
```

::: {.cell-output-display}
![](In-class_Ex04_files/figure-html/unnamed-chunk-6-1.png){width=672}
:::
:::

::: {.cell}

```{.r .cell-code}
car_resale <- read_xls("Data/ToyotaCorolla.xls",
                       "data")

car_resale
```

::: {.cell-output .cell-output-stdout}
```
# A tibble: 1,436 × 38
      Id Model       Price Age_0…¹ Mfg_M…² Mfg_Y…³     KM Quart…⁴ Weight Guara…⁵
   <dbl> <chr>       <dbl>   <dbl>   <dbl>   <dbl>  <dbl>   <dbl>  <dbl>   <dbl>
 1    81 TOYOTA Cor… 18950      25       8    2002  20019     100   1180       3
 2     1 TOYOTA Cor… 13500      23      10    2002  46986     210   1165       3
 3     2 TOYOTA Cor… 13750      23      10    2002  72937     210   1165       3
 4     3  TOYOTA Co… 13950      24       9    2002  41711     210   1165       3
 5     4 TOYOTA Cor… 14950      26       7    2002  48000     210   1165       3
 6     5 TOYOTA Cor… 13750      30       3    2002  38500     210   1170       3
 7     6 TOYOTA Cor… 12950      32       1    2002  61000     210   1170       3
 8     7  TOYOTA Co… 16900      27       6    2002  94612     210   1245       3
 9     8 TOYOTA Cor… 18600      30       3    2002  75889     210   1245       3
10    44 TOYOTA Cor… 16950      27       6    2002 110404     234   1255       3
# … with 1,426 more rows, 28 more variables: HP_Bin <chr>, CC_bin <chr>,
#   Doors <dbl>, Gears <dbl>, Cylinders <dbl>, Fuel_Type <chr>, Color <chr>,
#   Met_Color <dbl>, Automatic <dbl>, Mfr_Guarantee <dbl>,
#   BOVAG_Guarantee <dbl>, ABS <dbl>, Airbag_1 <dbl>, Airbag_2 <dbl>,
#   Airco <dbl>, Automatic_airco <dbl>, Boardcomputer <dbl>, CD_Player <dbl>,
#   Central_Lock <dbl>, Powered_Windows <dbl>, Power_Steering <dbl>,
#   Radio <dbl>, Mistlamps <dbl>, Sport_Model <dbl>, Backseat_Divider <dbl>, …
```
:::
:::

::: {.cell}

```{.r .cell-code}
model <- lm(Price ~ Age_08_04 + Mfg_Year + KM + 
              Weight + Guarantee_Period, data = car_resale)
model
```

::: {.cell-output .cell-output-stdout}
```

Call:
lm(formula = Price ~ Age_08_04 + Mfg_Year + KM + Weight + Guarantee_Period, 
    data = car_resale)

Coefficients:
     (Intercept)         Age_08_04          Mfg_Year                KM  
      -2.637e+06        -1.409e+01         1.315e+03        -2.323e-02  
          Weight  Guarantee_Period  
       1.903e+01         2.770e+01  
```
:::
:::


lm is an original R function building a linear regression model.


::: {.cell}

```{.r .cell-code}
tbl_regression(model,
               intercept = TRUE)
```

::: {.cell-output-display}
```{=html}
<div id="aqsntkpwxb" style="padding-left:0px;padding-right:0px;padding-top:10px;padding-bottom:10px;overflow-x:auto;overflow-y:auto;width:auto;height:auto;">
<style>html {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Helvetica Neue', 'Fira Sans', 'Droid Sans', Arial, sans-serif;
}

#aqsntkpwxb .gt_table {
  display: table;
  border-collapse: collapse;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 16px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #A8A8A8;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #A8A8A8;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}

#aqsntkpwxb .gt_heading {
  background-color: #FFFFFF;
  text-align: center;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#aqsntkpwxb .gt_caption {
  padding-top: 4px;
  padding-bottom: 4px;
}

#aqsntkpwxb .gt_title {
  color: #333333;
  font-size: 125%;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#aqsntkpwxb .gt_subtitle {
  color: #333333;
  font-size: 85%;
  font-weight: initial;
  padding-top: 0;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}

#aqsntkpwxb .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#aqsntkpwxb .gt_col_headings {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#aqsntkpwxb .gt_col_heading {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: normal;
  text-transform: inherit;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}

#aqsntkpwxb .gt_column_spanner_outer {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: normal;
  text-transform: inherit;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}

#aqsntkpwxb .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#aqsntkpwxb .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#aqsntkpwxb .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 5px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}

#aqsntkpwxb .gt_group_heading {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  text-align: left;
}

#aqsntkpwxb .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}

#aqsntkpwxb .gt_from_md > :first-child {
  margin-top: 0;
}

#aqsntkpwxb .gt_from_md > :last-child {
  margin-bottom: 0;
}

#aqsntkpwxb .gt_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}

#aqsntkpwxb .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 5px;
  padding-right: 5px;
}

#aqsntkpwxb .gt_stub_row_group {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 5px;
  padding-right: 5px;
  vertical-align: top;
}

#aqsntkpwxb .gt_row_group_first td {
  border-top-width: 2px;
}

#aqsntkpwxb .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#aqsntkpwxb .gt_first_summary_row {
  border-top-style: solid;
  border-top-color: #D3D3D3;
}

#aqsntkpwxb .gt_first_summary_row.thick {
  border-top-width: 2px;
}

#aqsntkpwxb .gt_last_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#aqsntkpwxb .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#aqsntkpwxb .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}

#aqsntkpwxb .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}

#aqsntkpwxb .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#aqsntkpwxb .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#aqsntkpwxb .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding-left: 4px;
  padding-right: 4px;
  padding-left: 5px;
  padding-right: 5px;
}

#aqsntkpwxb .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#aqsntkpwxb .gt_sourcenote {
  font-size: 90%;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
}

#aqsntkpwxb .gt_left {
  text-align: left;
}

#aqsntkpwxb .gt_center {
  text-align: center;
}

#aqsntkpwxb .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#aqsntkpwxb .gt_font_normal {
  font-weight: normal;
}

#aqsntkpwxb .gt_font_bold {
  font-weight: bold;
}

#aqsntkpwxb .gt_font_italic {
  font-style: italic;
}

#aqsntkpwxb .gt_super {
  font-size: 65%;
}

#aqsntkpwxb .gt_footnote_marks {
  font-style: italic;
  font-weight: normal;
  font-size: 75%;
  vertical-align: 0.4em;
}

#aqsntkpwxb .gt_asterisk {
  font-size: 100%;
  vertical-align: 0;
}

#aqsntkpwxb .gt_indent_1 {
  text-indent: 5px;
}

#aqsntkpwxb .gt_indent_2 {
  text-indent: 10px;
}

#aqsntkpwxb .gt_indent_3 {
  text-indent: 15px;
}

#aqsntkpwxb .gt_indent_4 {
  text-indent: 20px;
}

#aqsntkpwxb .gt_indent_5 {
  text-indent: 25px;
}
</style>
<table class="gt_table">
  
  <thead class="gt_col_headings">
    <tr>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1" scope="col" id="&lt;strong&gt;Characteristic&lt;/strong&gt;"><strong>Characteristic</strong></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_center" rowspan="1" colspan="1" scope="col" id="&lt;strong&gt;Beta&lt;/strong&gt;"><strong>Beta</strong></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_center" rowspan="1" colspan="1" scope="col" id="&lt;strong&gt;95% CI&lt;/strong&gt;&lt;sup class=&quot;gt_footnote_marks&quot;&gt;1&lt;/sup&gt;"><strong>95% CI</strong><sup class="gt_footnote_marks">1</sup></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_center" rowspan="1" colspan="1" scope="col" id="&lt;strong&gt;p-value&lt;/strong&gt;"><strong>p-value</strong></th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr><td headers="label" class="gt_row gt_left">(Intercept)</td>
<td headers="estimate" class="gt_row gt_center">-2,636,783</td>
<td headers="ci" class="gt_row gt_center">-3,150,331, -2,123,236</td>
<td headers="p.value" class="gt_row gt_center"><0.001</td></tr>
    <tr><td headers="label" class="gt_row gt_left">Age_08_04</td>
<td headers="estimate" class="gt_row gt_center">-14</td>
<td headers="ci" class="gt_row gt_center">-35, 7.1</td>
<td headers="p.value" class="gt_row gt_center">0.2</td></tr>
    <tr><td headers="label" class="gt_row gt_left">Mfg_Year</td>
<td headers="estimate" class="gt_row gt_center">1,315</td>
<td headers="ci" class="gt_row gt_center">1,059, 1,571</td>
<td headers="p.value" class="gt_row gt_center"><0.001</td></tr>
    <tr><td headers="label" class="gt_row gt_left">KM</td>
<td headers="estimate" class="gt_row gt_center">-0.02</td>
<td headers="ci" class="gt_row gt_center">-0.03, -0.02</td>
<td headers="p.value" class="gt_row gt_center"><0.001</td></tr>
    <tr><td headers="label" class="gt_row gt_left">Weight</td>
<td headers="estimate" class="gt_row gt_center">19</td>
<td headers="ci" class="gt_row gt_center">17, 21</td>
<td headers="p.value" class="gt_row gt_center"><0.001</td></tr>
    <tr><td headers="label" class="gt_row gt_left">Guarantee_Period</td>
<td headers="estimate" class="gt_row gt_center">28</td>
<td headers="ci" class="gt_row gt_center">3.8, 52</td>
<td headers="p.value" class="gt_row gt_center">0.023</td></tr>
  </tbody>
  
  <tfoot class="gt_footnotes">
    <tr>
      <td class="gt_footnote" colspan="4"><sup class="gt_footnote_marks">1</sup> CI = Confidence Interval</td>
    </tr>
  </tfoot>
</table>
</div>
```
:::
:::

::: {.cell}

```{.r .cell-code}
check_c <- check_collinearity(model)
plot(check_c)
```

::: {.cell-output-display}
![](In-class_Ex04_files/figure-html/unnamed-chunk-10-1.png){width=672}
:::
:::

::: {.cell}

```{.r .cell-code}
model_n <- lm(Price ~ Age_08_04 + KM + 
              Weight + Guarantee_Period, data = car_resale)
```
:::

::: {.cell}

```{.r .cell-code}
check_n <- check_normality(model_n)
plot(check_n)
```

::: {.cell-output-display}
![](In-class_Ex04_files/figure-html/unnamed-chunk-12-1.png){width=672}
:::
:::

::: {.cell}

```{.r .cell-code}
check_h <- check_heteroscedasticity(model_n)
plot(check_h)
```

::: {.cell-output-display}
![](In-class_Ex04_files/figure-html/unnamed-chunk-13-1.png){width=672}
:::
:::

::: {.cell}

```{.r .cell-code}
ggcoefstats(model_n, 
            output = "plot")
```

::: {.cell-output-display}
![](In-class_Ex04_files/figure-html/unnamed-chunk-14-1.png){width=672}
:::
:::


# Visualizing the uncertainty of point estimates: ggplot2 methods


::: {.cell}

```{.r .cell-code}
my_sum <- exam_data %>%
  group_by(RACE) %>%
  summarise(
    n=n(),
    mean=mean(MATHS),
    sd=sd(MATHS)
    ) %>%
  mutate(se=sd/sqrt(n-1))
```
:::

::: {.cell}

```{.r .cell-code}
knitr::kable(head(my_sum), format = 'html')
```

::: {.cell-output-display}
`````{=html}
<table>
 <thead>
  <tr>
   <th style="text-align:left;"> RACE </th>
   <th style="text-align:right;"> n </th>
   <th style="text-align:right;"> mean </th>
   <th style="text-align:right;"> sd </th>
   <th style="text-align:right;"> se </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> Chinese </td>
   <td style="text-align:right;"> 193 </td>
   <td style="text-align:right;"> 76.50777 </td>
   <td style="text-align:right;"> 15.69040 </td>
   <td style="text-align:right;"> 1.132357 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Indian </td>
   <td style="text-align:right;"> 12 </td>
   <td style="text-align:right;"> 60.66667 </td>
   <td style="text-align:right;"> 23.35237 </td>
   <td style="text-align:right;"> 7.041005 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Malay </td>
   <td style="text-align:right;"> 108 </td>
   <td style="text-align:right;"> 57.44444 </td>
   <td style="text-align:right;"> 21.13478 </td>
   <td style="text-align:right;"> 2.043177 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Others </td>
   <td style="text-align:right;"> 9 </td>
   <td style="text-align:right;"> 69.66667 </td>
   <td style="text-align:right;"> 10.72381 </td>
   <td style="text-align:right;"> 3.791438 </td>
  </tr>
</tbody>
</table>

`````
:::
:::

::: {.cell}

```{.r .cell-code}
ggplot(my_sum) +
  geom_errorbar(
    aes(x=RACE, 
        ymin=mean-se, 
        ymax=mean+se), 
    width=0.2, 
    colour="black", 
    alpha=0.9, 
    linewidth=0.5) +
  geom_point(aes
           (x=RACE, 
            y=mean), 
           stat="identity", 
           color="red",
           size = 1.5,
           alpha=1) +
  ggtitle("Standard error of mean 
          maths score by rac")
```

::: {.cell-output-display}
![](In-class_Ex04_files/figure-html/unnamed-chunk-17-1.png){width=672}
:::
:::

