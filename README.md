#include <iostream>
#include <fstream>
#include <string>

using namespace std;

int check(string u)
{
    string st;
    ifstream file(u + ".txt");
    file >> st;
    if (st == u)
        return 1;
    else
        return 0;
}

void login(string u, string p)
{
    string s;
    ifstream file(u + ".txt");

    if (!file)
    {
        cout << "NO USER FOUND" << endl;
    }
    else
    {
        while (1)
        {
            file >> s;
            if (file.eof())
                break;
            else
                continue;
        }
        if (s == u + p)
            cout << "\nLOGIN SUCCESSFULL";
        else
        {
            cout << "INCORRECT PASSWORD !!" << endl;
        }
    }
}

void reg(string un, string pw)
{
    fstream file;
    file.open(un + "." + "txt", ios_base::out);
    file << un;
    file << pw;
    file.close();
    cout << "PROFILE CREATED SUCCESSFULLY :]" << endl;
}

int main()
{
    string username, password;
    int choice, n;
    char restart;

    cout << "WELCOME TO THE PORTAL :)" << endl;
    cout << "1: LOGIN \n2: REGISTER \n3: EXIT" << endl;
    cin >> choice;

    switch (choice)
    {
    case 1:
        cout << "ENTER YOUR USERNAME: ";
        cin >> username;
        cout << "\nENTER THE PASSWORD: ";
        cin >> password;
        login(username, password);
        cout << "\nPress r to refresh" << endl;
        cin >> restart;
        if (restart == 'r')
            main();
        else
            break;
    case 2:
        cout << "ENTER THE USERNAME: ";
        cin >> username;
        n = check(username);
        if (n == 1)
            cout << "USERNAME EXISTS" << endl;
        else
        {
            cout << "\nENTER THE PASSWORD: ";
            cin >> password;
            reg(username, password);
        }
        cout << "\nPress r to refresh" << endl;
        cin >> restart;
        if (restart == 'r')
            main();
        else
            break;
    case 3:
        goto end;
        break;
    default:
        cout << "ENTER THE CORRECT CHOICE" << endl;
        break;
    }
    end:

    return 0;
}
