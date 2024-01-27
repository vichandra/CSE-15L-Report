> Using the command **cd** with no arguments takes us to the home directory. This is not an error and the working directory was /home. This happens even if you are in any other directories or subdirectories:
>
![Image](https://cdn.discordapp.com/attachments/974137838180380672/1196999964153364510/Screenshot_2024-01-11_at_9.06.21_AM.png?ex=65b9ac16&is=65a73716&hm=ac613cb613e028d5fd3733cbb29e8f6d9981005f57c4c5e91c9db57279c69afb&)



> When using **cd** with a directory as an argument, it changes the current directory to the directory of the argument. This is not an error, and the working directory is:
> /home/lecture1 :

![Image](https://cdn.discordapp.com/attachments/974137838180380672/1196999964430192661/Screenshot_2024-01-11_at_9.06.31_AM.png?ex=65b9ac16&is=65a73716&hm=5053c5b059fc2b573d39393d6966c90c9fe6d9e9bc9b1fcc5c71ee0ecc21575d&)



> Giving **cd** an argument to a path that leads to file or simply a file as an argument would not be a valid command because cd is meant to change to a different directory, not a different file, making it an error. The working directory in this case was: /home/lecture1

![Image](https://cdn.discordapp.com/attachments/974137838180380672/1196999964690235522/Screenshot_2024-01-11_at_9.06.38_AM.png?ex=65b9ac16&is=65a73716&hm=63b4eb601482a531085a94aadb770dbd82447dd7f99b1221a49ba3043806bf4e&)



> The **ls** commands lists the files or subdirectories that they are currently in. The current working directory is /home in this example and ls command does not result in an error. **ls** will lists all files or directories within home:

![Image](https://cdn.discordapp.com/attachments/974137838180380672/1196999964891553803/Screenshot_2024-01-11_at_9.08.04_AM.png?ex=65b9ac16&is=65a73716&hm=c6c7d7fa6cc36769c084cb1af8e9e9aa1ca2d34ad1da7742c5f3530a598393a7&)



> If the **ls** command is provided a directory as an argument, it will lists the contents of the directory which may include files or other directories contained within it. In this case the working directory is /home/lecture1 and calling the ls command int the case does not result in an error. That is what is happening when we provided lecture1 as an argument to the **ls** command:

![Image](https://cdn.discordapp.com/attachments/974137838180380672/1196999965097087107/Screenshot_2024-01-11_at_9.08.19_AM.png?ex=65b9ac16&is=65a73716&hm=7301e624ee19f14ab603fead049e467af292df492590a4e90a679fc7ed687a7a&)


> It appears that when the **ls** command is provided a file through a path, it lists the path again. In this case, the working directory was /home/lecture1. This is not an error because the point of **ls** is to litteraly list the contents:

![Image](https://cdn.discordapp.com/attachments/974137838180380672/1196999965394878554/Screenshot_2024-01-11_at_9.08.55_AM.png?ex=65b9ac16&is=65a73716&hm=ebe23c6954b4827c360af71fa57542f49c794a44c6786f17d0e95e3ba59180f7&)



> When using the **cat** command with a path to a file as an argument, the command will allow you to see the contents of the file. in this case, our current working directory was /home/lecture1/Hello.java and calling cat like this is not an error. it allows us to see the contents of Hello.java:

![Image](https://cdn.discordapp.com/attachments/974137838180380672/1197000003651112970/Screenshot_2024-01-11_at_9.12.35_AM.png?ex=65b9ac20&is=65a73720&hm=e316879ac120b71857646818e42146815d4d5537df086633b90b501a09ec2a58&)


> Typing in **cat** with no arguments it has nothing to read from the terminal, so it displays nothing. In this case, the current working directory was /home and there was no error:

![Image](https://cdn.discordapp.com/attachments/974137838180380672/1196999966317617173/Screenshot_2024-01-11_at_9.12.17_AM.png?ex=65b9ac17&is=65a73717&hm=9118927db0e9738bd4d70d9b5e61ed712b8c664a70aab129a3c448eada51b3e8&)



> if we give a directory to **cat** as an argument, it will confirm that is it a directory. In this case the working directory is /home/lecture1. It is not an error, it's just meant to display files on the command line, and you cannot display a directory on the command line with cat:

![Image](https://cdn.discordapp.com/attachments/974137838180380672/1197000003441410109/Screenshot_2024-01-11_at_9.12.29_AM.png?ex=65b9ac20&is=65a73720&hm=bbe74e68bf6602017552ca4f7bba3756faccfbd762a2239fe2f17c483a069595&)


