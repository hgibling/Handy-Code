emulate default ggplot colors:
```
gg.color.hue <- function(n) {
  hues = seq(15, 375, length = n + 1)
  hcl(h = hues, l = 65, c = 100)[1:n]
}
```

get last 3 colors of default 4
(when first value isn't plotted but you want the colors to match previous graph
```
gg.color.hue(4)[2:4]
```

replace all NAs in all columns:
```
mutate_all(~replace(., is.na(.), 0))
```

pass dplyr column names as variables:
```
df %>% mutate(MeanCOL=mean(.data[[COL]])
```

default R colors:
```
Red     DF536B
Green   61D04F
Blue    2297E6
Cyan    28E2E5
Magenta CD0BBC
Yellow  F5C710
Grey    9E9E9E
```
