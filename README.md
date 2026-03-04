#!/bin/bash 
# Function to create a file 
create_file() { 
    echo "Enter the filename to create:" 
    read filename 
    touch "$filename" 
    echo "File '$filename' created successfully!" 
} 
 
# Function to list files 
list_files() { 
    echo "Listing all files in the current directory:" 
    ls -lh 
} 
 
#  Function to process files 
process_files() { 
    echo "Choose file operation:" 
    echo "1. Search for a file" 
    echo "2. Copy a file" 
    echo "3. Delete a file" 
    read choice 
    case $choice in 
        1) 
            echo "Enter filename to search:" 
            read search_file 
            find . -name "$search_file" && echo "File found!" || echo "File not found!" 
            ;; 
        2) 
            echo "Enter the source file to copy:" 
            read src 
            echo "Enter the destination filename:" 
            read dest 
            cp "$src" "$dest" && echo "File copied successfully!" || echo "Error copying file!" 
            ;; 
        3) 
            echo "Enter filename to delete:" 
            read del_file 
            rm -i "$del_file" && echo "File deleted!" || echo "Error deleting file!" 
            ;; 
        *) 
            echo "Invalid choice!" 
            ;; 
    esac 
} 
 
# Function to manage users and groups 
user_group_management() { 
    echo "Choose user/group operation:" 
    echo "1. Create a new user" 
    echo "2. Create a new group" 
    read choice 
    case $choice in 
        1) 
            echo "Enter the username to create:" 
            read username 
            sudo useradd "$username" && echo "User '$username' created successfully!" || echo "Error creating user!" 
            ;; 
        2) 
            echo "Enter the group name to create:" 
            read groupname 
            sudo groupadd "$groupname" && echo "Group '$groupname' created successfully!" || echo "Error creating 
group!" 
            ;; 
        *) 
            echo "Invalid choice!" 
            ;; 
    esac 
} 
 
# Main menu 
while true; do 
    echo "===== File and User Management Script =====" 
    echo "1. Create a file" 
    echo "2. List files" 
    echo "3. Process files" 
    echo "4. Manage users and groups" 
    echo "5. Exit" 
    echo "Enter your choice:" 
    read option 
 
    case $option in 
        1) create_file ;; 
        2) list_files ;; 
        3) process_files ;; 
        4) user_group_management ;; 
        5) echo "Exiting script."; exit 0 ;; 
        *) echo "Invalid option! Please try again." ;; 
    esac 
done 
 
 
 
 
 
