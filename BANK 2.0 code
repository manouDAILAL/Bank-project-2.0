#include <iostream>
#include <string>
#include <vector>
#include <fstream>
#include <cctype>
#include <iomanip>

//users file name is : "usersfile.txt";
//client file name is : "clientfile.txt";

using namespace std;

struct permission {

    short showCleintlist = 1;
    short addNowClient = 2;
    short deletClient = 4;
    short updateClientInfo = 8;
    short findClient = 16;
    short transactionPage = 32;
    short systemManagment = 64;
};

struct ClientInfo {

    string AccountNumber;
    string PinCode;
    string ClientName;
    string Phone;
    double Balance;

};
struct systemUsers {

    string name;
    string password;
    int permessions;

};

systemUsers Read_user_Info() {

    systemUsers p;

    cout << "Enter users name : \n";
    getline(cin, p.name);

    cout << "Enter user passwoerd \n";
    cin >> p.password;

    cout << "Enter user permessions \n";
    cin >> p.permessions;

    return p;

}
systemUsers ReadUseerIdentity() {

    systemUsers p;

    cout << "Enter users name : ";
    getline(cin, p.name);

    cout << "Enter user passwoerd : ";
    cin >> p.password;
    cin.ignore();

    return p;

}

ClientInfo Read_Client_Info() {

    ClientInfo p;

    cout << "Enter client account number \n";
    cin >> p.AccountNumber;

    cout << "Enter pin code \n";
    cin >> p.PinCode;

    cin.ignore();
    cout << "Enter client name \n";
    getline(cin, p.ClientName);

    cout << "Enter phone number \n";
    cin >> p.Phone;

    cout << "Client balance \n";
    cin >> p.Balance;

    return p;

}

vector<systemUsers>systemAllUsers;
vector<ClientInfo>AllClient;

//__________________ data of client operation ________________________

ClientInfo organizingClientDateFromStringLineToStruct(string line) {

    ClientInfo p;
    vector <string> person;

    for (int i = 1; i <= 5; i++) {

        string info = "";
        size_t cutpoint = line.find("#//#");
        info = line.substr(0, cutpoint);
        person.push_back(info);
        line = line.erase(0, cutpoint + 4);

    }

    p.AccountNumber = person.at(0);
    p.PinCode = person.at(1);
    p.ClientName = person.at(2);
    p.Phone = person.at(3);
    p.Balance = stod(person.at(4));

    return p;

}
void extract_client_data() {

    fstream myfile;
    myfile.open("clientfile.txt", ios::in);

    if (myfile.is_open()) {

        string line = "";

        while (getline(myfile, line)) {

            AllClient.push_back(organizingClientDateFromStringLineToStruct(line));

        }
        myfile.close();
    }

}

string collect_client_info_in_one_line(const ClientInfo& p) {

    string InfoLine = "";

    InfoLine += p.AccountNumber + "#//#";
    InfoLine += p.PinCode + "#//#";
    InfoLine += p.ClientName + "#//#";
    InfoLine += p.Phone + "#//#";
    InfoLine += to_string(p.Balance) + "#//#";

    return InfoLine;
}
void storage_client_info_in_file() {

    fstream myfile;

    myfile.open("clientfile.txt", ios::out);

    if (myfile.is_open()) {

        for (ClientInfo& t : AllClient) {

            if (t.AccountNumber != "") {

                myfile << (collect_client_info_in_one_line(t)) << endl;

            }

        }
    }

    myfile.close();
}

//__________________ data of user operation ______________________________

systemUsers organizingUserDateFromStringLineToStruct(string line) {

    systemUsers p;
    vector <string> person;

    for (int i = 1; i <= 3; i++) {

        string info = "";
        size_t cutpoint = line.find("#//#");
        info = line.substr(0, cutpoint);
        person.push_back(info);
        line = line.erase(0, cutpoint + 4);

    }

    p.name = person.at(0);
    p.password = (person.at(1));
    p.permessions = stoi(person.at(2));


    return p;

}
void extract_user_data() {

    fstream myfile;
    myfile.open("usersfile.txt", ios::in);

    if (myfile.is_open()) {

        string line = "";

        while (getline(myfile, line)) {

            systemAllUsers.push_back(organizingUserDateFromStringLineToStruct(line));

        }
        myfile.close();
    }

}

string collect_user_info_in_one_line(const systemUsers& p) {

    string InfoLine = "";

    InfoLine += p.name + "#//#";
    InfoLine += p.password + "#//#";
    InfoLine += to_string(p.permessions) + "#//#";

    return InfoLine;
}
void storage_user_info_in_file() {

    fstream myfile;

    myfile.open("usersfile.txt", ios::out);

    if (myfile.is_open()) {

        for (systemUsers& t : systemAllUsers) {

            if (t.name != "") {

                myfile << (collect_user_info_in_one_line(t)) << endl;

            }

        }

    }

    myfile.close();
}

//_________________________________________________________________________

int selectOption(int numberofoptions, int option) {

    do {

        cout << "Choose what do you want to do [ 1 to " + to_string(numberofoptions) + " ]" << endl;
        cin >> option;

        if (cin.fail()) {

            cin.clear();
            cin.ignore(numeric_limits<streamsize>::max(), '\n');
            option = -1;

        }

    } while (option > numberofoptions || option < 1);

    return option;

}
void dashboard() {


    cout << string(60, '=') << endl;

    cout << string(20, ' ') + "Main Menu Screen" << endl;

    cout << string(60, '=') << endl;

    cout << string(8, ' ') + "[1] Show client list.\n";
    cout << string(8, ' ') + "[2] Add new client.\n";
    cout << string(8, ' ') + "[3] Delete client.\n";
    cout << string(8, ' ') + "[4] Update client info.\n";
    cout << string(8, ' ') + "[5] Find client.\n";
    cout << string(8, ' ') + "[6] transaction page.\n";
    cout << string(8, ' ') + "[7] system managment.\n";
    cout << string(8, ' ') + "[8] Logout.\n";

    cout << string(60, '=') << endl;

};

// ________________ clients and users operrations part _____________________

void showOneClientInfo_core_(ClientInfo& client) {

    cout << "______ " << client.ClientName << "______" << endl;

    cout << "AccountNumber : " << client.AccountNumber << endl;
    cout << "PinCode : " << client.PinCode << endl;
    cout << "ClientName : " << client.ClientName << endl;
    cout << "Phone : " << client.Phone << endl;
    cout << "Balance : " << client.Balance << endl;


}
void showOneUsersInfo_core_(systemUsers& user) {

    cout << "name : " << user.name << endl;
    cout << "password : " << user.password << endl;
    cout << "permessions : " << user.permessions << endl;

}

void showClientList_core_() {

    cout << string(100, '=') << endl;
    cout << "=" + string(40, ' ') + "Client Number is : (" + to_string(AllClient.size()) + ")" << string(36, ' ') + "=\n";
    cout << string(100, '=') << endl;
    cout << "=" << left << setw(18) << "  AccountNumber" << "=" << left << setw(18) << "  PinCode" << "=" << left << setw(20) << "  ClientName" << "=" << left << setw(19) << "  Phone" << "=" << left << setw(19) << "  Balance" << "=" << endl;
    cout << string(100, '=') << endl;

    for (ClientInfo& p : AllClient) {
        cout << "=" << left << setw(18) << " " + p.AccountNumber << "=" << left << setw(18) << " " + p.PinCode << "=" << left << setw(20) << " " + p.ClientName << "=" << left << setw(19) << " " + p.Phone << "=" << left << setw(19) << " " + to_string(p.Balance) << "=" << endl;
        cout << string(100, '=') << endl;

    }
}
void showUsersList_core_() {

    cout << string(100, '=') << endl;
    cout << "=" + string(40, ' ') + "Users Number is : (" + to_string(systemAllUsers.size()) + ")" << string(36, ' ') + "=\n";
    cout << string(100, '=') << endl;
    cout << "=" << left << setw(18) << "  name" << "=" << left << setw(18) << "  passwoerd" << "=" << left << setw(20) << "  permesions" << "=" << endl;
    cout << string(100, '=') << endl;

    for (systemUsers& p : systemAllUsers) {

        cout << "=" << left << setw(18) << " " + p.name << "=" << left << setw(18) << " " + p.password << "=" << left << setw(8) << " " << p.permessions << setw(10) << " " << "=" << endl;
        cout << string(100, '=') << endl;

    }
}

ClientInfo searchClientInClientsData_core_(string client_account_number) {



    ClientInfo person;
    person.AccountNumber = "not found";

    for (ClientInfo& p : AllClient) {

        if (p.AccountNumber == client_account_number) {
            person = p;
            return person;
        }

    }

    return person;


}
systemUsers searchUserInUsersList_core_(string userName) {

    systemUsers person;
    person.name = "not found";

    for (systemUsers& p : systemAllUsers) {

        if (p.name == userName) {

            person = p;
            return person;

        }

    }

    return person;
}

void deleteClient_core_(string client_account_number) {

    int counter = 0;

    for (ClientInfo& i : AllClient) {

        if (i.AccountNumber == client_account_number) {

            AllClient.at(counter) = { "" };
            cout << "\n Client deleted successfully " << endl;
        }

        counter++;
    }

}
void deletsystemuser_core_(string client_account_number) {

    int counter = 0;

    for (systemUsers& i : systemAllUsers) {

        if (i.name == client_account_number) {

            systemAllUsers.at(counter) = { "" };
            cout << "\n Client deleted successfully " << endl;

        }
        counter++;
    }

}

void updateClientInfo_core_(string client_account_number) {

    ClientInfo client_data;
    ClientInfo copy_client_data;

    client_data = searchClientInClientsData_core_(client_account_number);

    int options = 0;

    cout << endl;

    showOneClientInfo_core_(client_data);

    cout << "\n\n";
    cout << "What information you want to modify ? \n [1] PinCode . \n[2] Client Name . \n[3] Phone .\n[4] Balance \n";

    do {
        cin >> options;
    } while (options > 4 || options < 1);
    {
        copy_client_data.AccountNumber = client_data.AccountNumber;

        if (options == 1) {
            cout << "Enter pin code \n";
            cin >> copy_client_data.PinCode;
            copy_client_data.ClientName = client_data.ClientName;
            copy_client_data.Phone = client_data.Phone;
            copy_client_data.Balance = client_data.Balance;
        }

        else if (options == 2) {

            cin.ignore();
            cout << "Enter client name \n";
            getline(cin, copy_client_data.ClientName);

            copy_client_data.PinCode = client_data.PinCode;
            copy_client_data.Phone = client_data.Phone;
            copy_client_data.Balance = client_data.Balance;
        }

        else if (options == 3) {
            cout << "Enter phone number \n";
            cin >> copy_client_data.Phone;
            copy_client_data.ClientName = client_data.ClientName;
            copy_client_data.PinCode = client_data.PinCode;
            copy_client_data.Balance = client_data.Balance;
        }

        else if (options == 4) {
            cout << "Client balance \n";
            cin >> copy_client_data.Balance;
            copy_client_data.ClientName = client_data.ClientName;
            copy_client_data.Phone = client_data.Phone;
            copy_client_data.PinCode = client_data.PinCode;
        }
    }

    deleteClient_core_(client_data.AccountNumber);
    AllClient.push_back(copy_client_data);
}
void updateUserInfo_core_(string client_account_number) {

    systemUsers client_data;
    systemUsers copy_client_data;

    client_data = searchUserInUsersList_core_(client_account_number);

    int options = 0;

    cout << endl;

    showOneUsersInfo_core_(client_data);

    cout << "\n\n";
    cout << "What information you want to modify ? \n[1] password . \n[2] permesions\n";

    do {

        cin >> options;

    } while (options > 4 || options < 1);

    {
        copy_client_data.name = client_data.name;

        if (options == 1) {

            cout << "Enter new password : \n";
            cin >> copy_client_data.password;
            copy_client_data.permessions = client_data.permessions;

        }

        else if (options == 2) {

            cout << "Enter new persmession \n";
            cin >> copy_client_data.permessions;

            copy_client_data.password = client_data.password;
        }
    }

    deleteClient_core_(client_data.name);
    systemAllUsers.push_back(copy_client_data);
}

void addNewClient_core_(string operationType) {

    if (operationType == "ClientInfo") {

        ClientInfo p;
        p = Read_Client_Info();
        AllClient.push_back(p);

    }
    else if (operationType == "systemUsers") {

        systemUsers p;
        p = Read_user_Info();
        systemAllUsers.push_back(p);

    }

}

// __________________ transaction mangment part ____________________________

void transaction_dashboard() {

    cout << string(60, '=') << endl;

    cout << string(20, ' ') + "transaction Screen" << endl;

    cout << string(60, '=') << endl;

    cout << string(8, ' ') + "[1] Deposit.\n";
    cout << string(8, ' ') + "[2] Withdraw .\n";
    cout << string(8, ' ') + "[3] total balances .\n";
    cout << string(8, ' ') + "[4] main menue .\n";

    cout << string(60, '=') << endl;


}
void update_client_balance(ClientInfo client, int new_balance, string type_of_transaction) {

    if (type_of_transaction == "Deposit") {

        client.Balance += new_balance;

        deleteClient_core_(client.AccountNumber);
        AllClient.push_back(client);

        cout << "Done successfully" << endl;

    }
    else if (type_of_transaction == "Withdraw") {

        if (client.Balance >= new_balance) {

            client.Balance -= new_balance;
            deleteClient_core_(client.AccountNumber);
            AllClient.push_back(client);

        }
        else if (client.Balance < new_balance) {

            cout << "Balance unavailable" << endl;

        }
    }

}
void show_clients_balances(vector<ClientInfo>& cleints_final_info_after_process) {

    cout << string(100, '=') << endl;
    cout << "=" + string(40, ' ') + "Client Number is : (" + to_string(cleints_final_info_after_process.size()) + ")" << string(36, ' ') + "=\n";
    cout << string(100, '=') << endl;
    cout << "=" << left << setw(18) << "  AccountNumber" << "=" << left << setw(20) << "  ClientName" << "=" << left << setw(19) << "  Balance" << "=" << endl;
    cout << string(100, '=') << endl;

    for (ClientInfo& p : cleints_final_info_after_process) {
        cout << "=" << left << setw(18) << " " + p.AccountNumber << "=" << left << setw(20) << " " + p.ClientName << "=" << left << setw(19) << " " + to_string(p.Balance) << "=" << endl;
        cout << string(100, '=') << endl;

    }
}

void deposit() {

    system("cls");

    ClientInfo client;
    string clientAccountNumber;

    cout << "enter client account number : ";
    cin >> clientAccountNumber;

    client = searchClientInClientsData_core_(clientAccountNumber);

    if (client.AccountNumber == "not found") {

        cout << "client not find !" << endl;
        system("pause");

    }
    else if (client.AccountNumber != "not found") {

        double newDiposit = 0;
        cout << "enter now client diposit : ";
        cin >> newDiposit;

        client.Balance += newDiposit;

        deleteClient_core_(client.AccountNumber);
        AllClient.push_back(client);

        cout << "operation done\n" << endl;
        system("pause");
    }


}
void Withdraw() {

    system("cls");

    ClientInfo client;
    string clientAccountNumber;

    cout << "enter client account number : ";
    cin >> clientAccountNumber;

    client = searchClientInClientsData_core_(clientAccountNumber);

    if (client.AccountNumber == "not found") {

        cout << "client not find !" << endl;
        system("pause");

    }
    else if (client.AccountNumber != "not found") {

        double Withdraw = 0;
        cout << "enter now client Withdraw : ";
        cin >> Withdraw;

        client.Balance -= Withdraw;

        deleteClient_core_(client.AccountNumber);
        AllClient.push_back(client);

        cout << "operation done\n" << endl;
        system("pause");
    }


}
void totalbalances() {

    if (AllClient.empty()) {

        cout << "number of client is 0 . add client first ." << endl;
    }
    else {

        showClientList_core_();
    }

    double totaleBlances = 0;

    for (ClientInfo& p : AllClient) {
        totaleBlances += p.Balance;
    }

    cout << " -----> totale of balances is : " << totaleBlances << endl;

    system("pause");
}

//___________________ authentication user part _____________________________

void systemManagmentDashbord() {

    cout << string(60, '=') << endl;

    cout << string(20, ' ') + "authentication Screen" << endl;

    cout << string(60, '=') << endl;

    cout << string(8, ' ') + "[1] user list .\n";
    cout << string(8, ' ') + "[2] add user .\n";
    cout << string(8, ' ') + "[3] delet user .\n";
    cout << string(8, ' ') + "[4] update user  .\n";
    cout << string(8, ' ') + "[5] finde user  .\n";
    cout << string(8, ' ') + "[6] Back to menue  .\n";

    cout << string(60, '=') << endl;

}
bool userAuthenticaition(systemUsers user) {

    systemUsers p;
    p = searchUserInUsersList_core_(user.name);
    return (p.name == user.name && p.password == user.password);

}
bool isUserHavePermission(systemUsers user, short userpermission) {
    return ((user.permessions & userpermission) != 0);
}

//__________________________________________________________________________

systemUsers currentUser() {

    systemUsers person, currentAllInfo;

    do {

        person = ReadUseerIdentity();
        if (!userAuthenticaition(person)) {

            cout << endl << "information is not right !! \n";
            system("pause");
            system("cls");

        }

    } while (!userAuthenticaition(person));

    return currentAllInfo = searchUserInUsersList_core_(person.name);
}

void addNowClient(systemUsers user) {

    permission addClientPermession;
    if (isUserHavePermission(user, addClientPermession.addNowClient)) {

        addNewClient_core_("ClientInfo");
        cout << "done ." << endl;
        system("pause");
    }
    else {
        system("cls");
        cout << "you dont have permession to do this operation" << endl;
    }

}
void showClientList(systemUsers user) {

    permission addClientPermession;

    if (isUserHavePermission(user, addClientPermession.showCleintlist)) {

        if (AllClient.empty()) {

            cout << "number of client is 0 . add client first ." << endl;
        }
        else {

            showClientList_core_();
        }

        system("pause");
    }
    else {

        system("cls");
        cout << "you dont have permession to do this operation" << endl;

    }
}
void deletClient(systemUsers user) {

    permission addClientPermession;

    if (isUserHavePermission(user, addClientPermession.deletClient)) {

        ClientInfo client;
        string clientAccountNumber;

        cout << "enter client account number : ";
        cin >> clientAccountNumber;

        client = searchClientInClientsData_core_(clientAccountNumber);

        if (client.AccountNumber == "not found") {

            cout << "client not find !" << endl;
            system("pause");

        }
        else if (client.AccountNumber != "not found") {

            showOneClientInfo_core_(client);
            system("pause");

            deleteClient_core_(client.AccountNumber);
            cout << "done ." << endl;
            system("pause");

        }
    }
    else {

        system("cls");
        cout << "you dont have permession to do this operation" << endl;
    }
}
void updateClientInfo(systemUsers user) {

    permission addClientPermession;

    if (isUserHavePermission(user, addClientPermession.updateClientInfo)) {

        ClientInfo client;
        string clientAccountNumber;

        cout << "enter client account number : ";
        cin >> clientAccountNumber;

        client = searchClientInClientsData_core_(clientAccountNumber);

        if (client.AccountNumber == "not found") {
            cout << "client not find !" << endl;
            system("pause");
        }
        else if (client.AccountNumber != "not found") {

            showOneClientInfo_core_(client);
            updateClientInfo_core_(client.AccountNumber);
            cout << "done ." << endl;
            system("pause");

        }

    }
    else {
        system("cls");
        cout << "you dont have permession to do this operation" << endl;
    }

}
void findclient(systemUsers user) {

    permission addClientPermession;
    if (isUserHavePermission(user, addClientPermession.findClient)) {

        ClientInfo client;
        string clientAccountNumber;

        cout << "enter client account number : ";
        cin >> clientAccountNumber;

        client = searchClientInClientsData_core_(clientAccountNumber);

        if (client.AccountNumber == "not found") {

            cout << "client not find !" << endl;
            system("pause");

        }
        else if (client.AccountNumber != "not found") {

            showOneClientInfo_core_(client);
            system("pause");

        }
    }
    else {

        system("cls");
        cout << "you dont have permession to do this operation" << endl;
    }
}

void adduser() {

    addNewClient_core_("systemUsers");
    cout << "done ." << endl;
    system("pause");

}
void userslist() {

    if (systemAllUsers.empty()) {

        cout << "number of client is 0 . add client first ." << endl;
    }
    else {

        showUsersList_core_();
    }

    system("pause");
}
void deletUser() {

    systemUsers User;
    string clientAccountNumber;

    cout << "enter user name : ";
    cin >> clientAccountNumber;

    User = searchUserInUsersList_core_(clientAccountNumber);

    if (User.name == "not found") {

        cout << "user not find !" << endl;
        system("pause");

    }
    else if (User.name != "not found") {

        showOneUsersInfo_core_(User);
        system("pause");
        deletsystemuser_core_(User.name);
        cout << "done ." << endl;
        system("pause");

    }
}
void updateUser() {

    systemUsers User;
    string clientAccountNumber;

    cout << "enter client account number : ";
    cin >> clientAccountNumber;

    User = searchUserInUsersList_core_(clientAccountNumber);

    if (User.name == "not found") {

        cout << "User not find !" << endl;
        system("pause");

    }
    else if (User.name != "not found") {

        showOneUsersInfo_core_(User);
        updateUserInfo_core_(User.name);
        cout << "done ." << endl;
        system("pause");

    }

}
void findeUser() {

    systemUsers User;
    string clientAccountNumber;

    cout << "enter client account number : ";
    cin >> clientAccountNumber;

    User = searchUserInUsersList_core_(clientAccountNumber);

    if (User.name == "not found") {

        cout << "user not find !" << endl;
        system("pause");

    }
    else if (User.name != "not found") {

        showOneUsersInfo_core_(User);
        system("pause");

    }

}

void transactionPage(systemUsers user) {

    permission addClientPermession;

    if (isUserHavePermission(user, addClientPermession.transactionPage)) {

        int option = 0;
        int storpPoint = 1;

        do {

            system("cls");
            transaction_dashboard();

            switch (selectOption(4, option)) {

            case 1: system("cls"); deposit(); break;
            case 2: system("cls"); Withdraw(); break;
            case 3: system("cls"); totalbalances(); break;
            case 4: storpPoint = -1; break;

            };

        } while (storpPoint > 0);

    }
    else {

        system("cls");
        cout << "you dont have permession to do this operation" << endl;
    }
}
void systemManagmentPage(systemUsers user) {

    permission addClientPermession;

    if (isUserHavePermission(user, addClientPermession.systemManagment)) {

        int option = 0;
        int storpPoint = 1;

        do {

            system("cls");
            systemManagmentDashbord();

            switch (selectOption(6, option)) {

            case 1: system("cls"); userslist(); break;
            case 2: system("cls"); adduser(); break;
            case 3: system("cls"); deletUser(); break;
            case 4: system("cls"); updateUser(); break;
            case 5: system("cls"); findeUser(); break;
            case 6: storpPoint = -1; break;

            };

        } while (storpPoint > 0);

    }

    else {

        system("cls");
        cout << "you dont have permession to do this operation" << endl;
    }
}

void organaizeFanctionsCalls(systemUsers user) {

    int option = 0;
    int storpPoint = 1;

    do {
        system("cls");
        dashboard();

        switch (selectOption(8, option)) {

        case 1:  system("cls"); showClientList(user); break;
        case 2: system("cls"); addNowClient(user); break;
        case 3:  system("cls"); deletClient(user); break;
        case 4:  system("cls"); updateClientInfo(user); break;
        case 5:  system("cls"); findclient(user); break;
        case 6:  system("cls"); transactionPage(user); break;
        case 7: system("cls"); systemManagmentPage(user); break;
        case 8: storpPoint = -1;

        };

    } while (storpPoint > 0);

}

int main()

{

    int storpPoint = 0;

    do {

        systemAllUsers.clear();
        AllClient.clear();

        extract_client_data();
        extract_user_data();

        systemUsers user;

        do {
            system("cls");

            user = ReadUseerIdentity();

            if (userAuthenticaition(user) == false) {

                cout << "\nincorrect information !" << endl;
                system("pause");

            }

        } while (userAuthenticaition(user) == false);

        user = searchUserInUsersList_core_(user.name);

        organaizeFanctionsCalls(user);

        storage_client_info_in_file();
        storage_user_info_in_file();

        cin.ignore();

    } while (storpPoint == 0);

    //systemAllUsers.clear();
    //adduser();
    //storage_user_info_in_file();

}
