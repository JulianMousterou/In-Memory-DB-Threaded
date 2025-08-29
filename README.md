# In-Memory-DB-Threaded
In memory database server/client that communicate over TCP. Written in C++ and only around ~800 lines of code. 

## Usage

      #include "/home/shark/code/projects/in-memory-db/include/clientclass.h
      int main() {
        Client db;
        db.ClientStart();
        db.sendReq("PUT HASHMAP key1\n"); 
        db.sendReq("PUTIN HASHMAP key1 passwords 1.23456\n");
        db.sendReq("GET HASHMAP key1 passwords\n");
        db.sendReq("SAVE\n");
        float result = db.recvIntoFloat(); 
        float result2 = result - 0.03456;
        std::cout<<"\nGot:"<<result<<"\nAlso\n"<<result2<<std::endl; 
      }

To start the server, create an object of class "Client", and then call "ClientStart()" on that object to start the server. It binds to INADDR_ANY by default so localhost will automatically work. The database uses strings for all storage types, if a different type is needed you can make a GET request and then call "recvIntoInt" for example. SAVE will save the current data into a JSON file.
