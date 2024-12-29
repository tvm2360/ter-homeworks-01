# ter-homeworks/01
![Terraform version](https://github.com/user-attachments/assets/4f8d484d-60e3-4a07-9af3-2fb54769c0e8)
![Docker version](https://github.com/user-attachments/assets/adb86a2c-032d-4715-a1c1-d7aaf93ff5bf)

## Задание 1
2. Допустимое хранение в personal.auto.tfvars
3. Sensisitve data:
 
![Sensitive](https://github.com/user-attachments/assets/70ee80dd-7591-4e35-a723-8fb915a40ce2)

Key:value:

![Result](https://github.com/user-attachments/assets/bc7a1e06-f47b-4d00-914a-9beee420a31a)

4. Ошибки:
   
![Error](https://github.com/user-attachments/assets/7fae13a0-c09b-46fc-bf43-da998c903875)

   - для типа объекта "docker_image" отсутствует его уникальное имя
   - для типа объекта "docker_container" его уникальное имя должно начинаться с буквы или символа подчёркивания и содержать только буквы, цифры, символы подчёркивания и тире

![Error_1](https://github.com/user-attachments/assets/c1f7ed3c-89f3-44b6-8d64-3d77174debe9)
     
   - для ресурса random_password, random_string_FAKE не задекларирована


