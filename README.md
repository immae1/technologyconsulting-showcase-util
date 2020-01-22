# showcase-util
The deployment project where all EAR files of the showcase are deployed together on the open liberty server.

## configuration
could be found in resources/liberty/config/server.xml

## basic setup or smoke test
Please use the smoketest setup-db.sh scripts of the corresponding domain parent project in following order to do a basic setup

- [supplierdomain/resources/smoketest/setup-db.sh](https://github.com/NovatecConsulting/technologyconsulting-showcase-supplierdomain/blob/master/resources/smoketest/setup-db.sh)
- [manufacturedomain/resources/smoketest/setup-db.sh](https://github.com/NovatecConsulting/technologyconsulting-showcase-manufacturedomain/blob/master/resources/smoketest/setup-db.sh)
- [orderdomain/resources/smoketest/setup-db.sh](https://github.com/NovatecConsulting/technologyconsulting-showcase-orderdomain/blob/master/resources/smoketest/setup-db.sh)

after the basic setup you can use the business-call.sh script (or the curl calls inside the script) in the smoketest folder. The business-call.sh script also start/stop the mockserver which is not really in this project but it does not conflict with open liberty so far.

Be aware that the corresponding domain objects have to exist for a call otherwiese you get a error from the call. The three domains will interact with each other during the execution of the smoke test. The setup during the smoke test will fit together over the three domains. i.e. the item id in order domain is corresponding to the assembly id in the manufacture domain which itself corresponds to the supplier_component id in the supplier domain.

## build, run and stop supplierdomain on an open liberty server
- **build:** mvn clean install
- **run:** mvn liberty:run
- **stop:** mvn liberty:stop
- **run open liberty in development mode:** mvn liberty:dev

## openAPI
check [openAPI](http://localhost:9080/api/explorer/) if the server is running for the full API of all three domains