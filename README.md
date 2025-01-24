# **Harvest Writeup**

**Important:**

I don't want money for that!

## Passwords

| User  | Password               |  Type      |
| ----- | -----------------------|----------- |
| user | butiamadmin | admin |
| administrator | admin | user |
| root  | hardestharvest | admin |


## Brute forcing for easy credentials and logging in.
- Open the Terminal/Shell/Console.
  
![img](/Terminal.png)

- Create two wordlists manually.

**Like:**

admin

root

user

john

administrator

harvest

guest...

--------------


administartor

admin

user

butiamadmin

1234

123456

harvest

hardest

hardestharvest...

---------------

- Let's "**HYDRA**"!

  ![img](/Hydra.png)
  
```bash
hydra-wizard
```

After that, use admin or user credentials for loging in with ssh. Try sudo su, sudo nano /etc/sudoers, nano /etc/sudoers or su.

**And you have access!**

You can select a difficulty for my machine.
