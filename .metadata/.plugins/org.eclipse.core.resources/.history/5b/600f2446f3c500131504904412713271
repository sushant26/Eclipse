@RestResource(urlMapping='/Account/*')
global with sharing class ACRDetails {
  
@HttpGet
    global static List<CustomerContactRoleWrapper> doGet(RestRequest req) {
        //RestRequest req = RestContext.request;
        //RestResponse res = RestContext.response;
        
        //String accountId = req.requestURI.substring(req.requestURI.lastIndexOf('/')+1);
        String accountId =  req.params.get('account_name');
   if(accountId != null && accountId != ''){
        //List<String> reqParameters=req.split('//');
        //Pattern MyTestPattern = Pattern.compile('')
        //for(Integer i=0;i<reqParameters.size();i++){
          
        //}
        Integer accLength = accountId.length();
        Integer remLength = 10 - accLength;
        String tempLength='';
        if(accountId.length() < 10){
          for(Integer i = 0; i < remLength; i++){
            tempLength +='0';
          }
          accountId = tempLength + accountId; 
        }
        System.debug('@@@account'+accountId);
        //Account result = [SELECT Id, Name, Phone, Website FROM Account WHERE Id = :accountId];
        List<Account_Contact_Role__c> conRoleList = [Select a.Title__c,a.CableUnit__c,a.Role__r.Name,a.Role__r.Code__c,a.Contact__c,a.Contact__r.Phone,a.Contact__r.Email,a.Contact__r.MobilePhone,a.Total_Insight__c,a.Contact__r.Company_Customer__c,a.Contact__r.Title,a.Contact__r.Name,a.Contact__r.FirstName,a.Contact__r.LastName,a.Contact__r.HomePhone,a.Contact__r.Street_P__r.PO_Box__c,a.Contact__r.Street_P__r.Town__c,a.Contact__r.Street_P__r.Postcode__c,a.Contact__r.Street_P__r.Door_No__c,a.Contact__r.Street_P__r.House_No__c,a.Contact__r.Street_P__r.Entrance__c,a.Contact__r.Street_P__r.Street__c,a.Contact__r.Street_P__r.Floor__c,a.Contact__r.Street_P__r.Side__c,a.Contact__r.Street_P__r.District__c From Account_Contact_Role__c a where a.cableunit__c =:accountId];
        return mapToWrapperList(conRoleList);
     }else{
       //RestRequest request1 = RestContext.request;
        //RestResponse response1 = RestContext.response;
        //response1.statusCode = 400;
        return new List<CustomerContactRoleWrapper>();
     }
        
    }
    
    private static List<CustomerContactRoleWrapper> mapToWrapperList(List<Account_Contact_Role__c> listcf){
    List<CustomerContactRoleWrapper> listWrapper = new List<CustomerContactRoleWrapper>();
    for(Account_Contact_Role__c cf : listcf){
        CustomerContactRoleWrapper cfWrapper = new CustomerContactRoleWrapper();
        cfWrapper.cableUnitNumber = cf.CableUnit__c;
        if(cf.Total_Insight__c != null && cf.Total_Insight__c != ''){
          cfWrapper.numberOfMagazies = Integer.valueOf(cf.Total_Insight__c);
        }
        //cfWrapper.numberOfMagazies = 0; //Integer.valueOf(cf.Total_Insight__c);// check if not null
    cfWrapper.contactId = cf.Contact__c;
        cfWrapper.title = cf.Contact__r.Title;
        cfWrapper.email = cf.Contact__r.Email;
        cfWrapper.fullName = cf.Contact__r.Name;
        cfWrapper.firstName = cf.Contact__r.FirstName;
        cfWrapper.lastName = cf.Contact__r.LastName;  
        cfWrapper.organization = cf.Contact__r.Company_Customer__c;
        cfWrapper.workPhone = cf.Contact__r.Phone;
        cfWrapper.mobilePhone = cf.Contact__r.MobilePhone;
        cfWrapper.privatePhone = cf.Contact__r.HomePhone;
        cfWrapper.roleCode = cf.Role__r.Code__c;
        cfWrapper.roleName = cf.Role__r.Name;
        cfWrapper.roleId = cf.Role__c;
        cfWrapper.streetName = cf.Contact__r.Street_P__r.Street__c;
        cfWrapper.floor = cf.Contact__r.Street_P__r.Floor__c;
        cfWrapper.doorNo = cf.Contact__r.Street_P__r.Door_No__c;   
        cfWrapper.entrance = cf.Contact__r.Street_P__r.Entrance__c;
        cfWrapper.houseNo = cf.Contact__r.Street_P__r.House_No__c;
        cfWrapper.postCode = cf.Contact__r.Street_P__r.Postcode__c;
        cfWrapper.town =  cf.Contact__r.Street_P__r.Town__c;
        cfWrapper.POBoxNr =  cf.Contact__r.Street_P__r.PO_Box__c;
        cfWrapper.locality = cf.Contact__r.Street_P__r.District__c;
        listWrapper.add(cfWrapper);
    }
    return listWrapper;
}


    

global class CustomerContactRoleWrapper {
   public String cableUnitNumber;
   public Integer numberOfmagazies;
   public String contactId;
   public String title;
   public String email;
   public String fullName;
   public String firstName;
   public String lastName;
   public String organization;
   public String workPhone;
   public String mobilePhone;
   public String privatePhone;
   public String roleCode;
   public String roleName;
   public String roleId;  
   public String streetName;   
   public String floor;
   public String doorNo;
   public String entrance;
   public String houseNo;
   public String postCode;    
   public String town;
   public String POBoxNr;
   public String locality;
   
}


}