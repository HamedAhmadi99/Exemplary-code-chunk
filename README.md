# Description: 
The provided code snippet is part of the Wave VII Maghreb Dataset project, focusing on transforming measures related to democracy in Algeria, Mauritania, Morocco, and Tunisia. It includes variables such as "Economic Performance Under Democracy," "Decisiveness of Democratic Regimes," "Effectiveness of Democratic Systems," and "Comparative Advantage of Democracy." These variables assess public perceptions of the impact of democracy on various aspects like economic performance and effectiveness in governance. The responses were recoded using a reversed scoring method, turning numerical responses into categorical factors to better represent levels of agreement or disagreement with the survey statements. This method clarifies the data and enhances the analysis of socio-political sentiments in these countries.


# Clean the 4 measures of satisfaction/preference for democracy
df <- df %>%
  mutate(
    Q516_1_num = case_when(
      Q516_1 == 1 ~ 4,
      Q516_1 == 2 ~ 3,
      Q516_1 == 3 ~ 2,
      Q516_1 == 4 ~ 1,
      TRUE ~ NA_real_  
    ),
    Q516_2_num = case_when(
      Q516_2 == 1 ~ 4,
      Q516_2 == 2 ~ 3,
      Q516_2 == 3 ~ 2,
      Q516_2 == 4 ~ 1,
      TRUE ~ NA_real_
    ),
    Q516_3_num = case_when(
      Q516_3 == 1 ~ 4,
      Q516_3 == 2 ~ 3,
      Q516_3 == 3 ~ 2,
      Q516_3 == 4 ~ 1,
      TRUE ~ NA_real_
    ),
    Q516_4_num = case_when(
      Q516_4 == 1 ~ 4,
      Q516_4 == 2 ~ 3,
      Q516_4 == 3 ~ 2,
      Q516_4 == 4 ~ 1,
      TRUE ~ NA_real_
    )
  )


df <- df %>%
  mutate(
    Q516_1 = factor(
      Q516_1_num,
      levels = c(1, 2, 3, 4),
      labels = c("Strongly disagree", "Disagree", "Agree", "Strongly agree")
    ),
    Q516_2 = factor(
      Q516_2_num,
      levels = c(1, 2, 3, 4),
      labels = c("Strongly disagree", "Disagree", "Agree", "Strongly agree")
    ),
    Q516_3 = factor(
      Q516_3_num,
      levels = c(1, 2, 3, 4),
      labels = c("Strongly disagree", "Disagree", "Agree", "Strongly agree")
    ),
    Q516_4 = factor(
      Q516_4_num,
      levels = c(1, 2, 3, 4),
      labels = c("Strongly disagree", "Disagree", "Agree", "Strongly agree")
    )
  ) %>%
  select(-matches("_num$"))  


table(df$Q516_1)
table(df$Q516_2)
table(df$Q516_3)
table(df$Q516_4)
