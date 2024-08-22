# Active Directory with PowerShell

This project showcases the automation of Active Directory (AD) setup and management using PowerShell in a virtualized environment. The focus is on configuring Windows Server 2019 as a Domain Controller for `semaye.com`, implementing essential network services, and streamlining the management of user accounts and organizational units.

## Project Description


![image](https://github.com/user-attachments/assets/36a3ce56-f774-470d-8ef2-048abaa6414e)


In this project, Windows Server 2019 is configured as a Domain Controller (DC) within a VirtualBox environment. The project involves setting up NAT services and DHCP to facilitate seamless communication between virtual machines. User accounts, groups, and organizational units are created and managed to control access efficiently. The project highlights automation by using PowerShell scripting to create 1000 user accounts, demonstrating the scalability and efficiency of managing large AD environments.

## Tools and Technologies

- **Windows Server 2019**: Used as the Domain Controller.
- **Windows 10**: Used as client machines integrated into the AD domain.
- **PowerShell**: Scripting language used for automation of tasks, including the bulk creation of user accounts.
- **VirtualBox**: Virtualization software used to create and manage the virtual environment.
- **Active Directory Domain Services (AD DS)**: The directory service provided by Microsoft for Windows domain networks.
- **DHCP (Dynamic Host Configuration Protocol)**: Automatically assigns IP addresses to client machines within the network.
- **NAT (Network Address Translation)**: Configured to enable network connectivity and manage IP addressing within the virtual environment.

## Use Cases

- **Domain Controller Configuration**: Demonstrates how to set up a Windows Server as a Domain Controller, which is fundamental in managing network resources and security within a domain.
- **User and Group Management**: Provides a template for creating and managing user accounts, groups, and organizational units, essential for any IT infrastructure relying on Active Directory.
- **Automation with PowerShell**: Shows how PowerShell can be leveraged to automate repetitive tasks like bulk user creation, which is particularly useful in large-scale enterprise environments.
- **Network Services Configuration**: Includes the implementation of NAT and DHCP services to ensure proper network functionality within a virtualized environment.

## Conclusion

This project serves as a practical guide for IT professionals and students interested in learning how to efficiently manage Active Directory environments using PowerShell. By automating critical tasks and ensuring proper network configuration, this setup can be adapted for real-world enterprise environments or educational purposes.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.
