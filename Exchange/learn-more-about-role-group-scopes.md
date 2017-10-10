---
title: Learn more about role group scopes
ms.prod: EXCHANGE
ms.assetid: 8e51557e-f7a0-472d-88e3-04432c5dfdea
---


# Learn more about role group scopes

Management role scopes enable you to define the specific scope of impact or influence of a management role when a management role assignment is created. When you apply a scope, the role assignee assigned to the role can only modify the objects contained within that scope. This can be helpful if you want members of the role group to manage only a certain set of users or resources. For more information about role scopes, see  [Understanding Management Role Scopes](http://technet.microsoft.com/library/24ed4a38-438a-4223-9f9c-5d4dea4b046b.aspx).
  
    
    

An implicit write scope is the scope that's applied to a role if no other scope is selected. If you don't create any other scopes, the only scope available for selection from the **Write scope** field is **Default**. If you've created additional scopes, you can select one of the scopes and the scope will be applied to all the roles that are assigned to the role group. The scope you select will override the implicit write scope defined on the role. For more information about implicit write scopes, see "Implicit scopes" in  [Understanding Management Role Scopes](http://technet.microsoft.com/library/24ed4a38-438a-4223-9f9c-5d4dea4b046b.aspx).
To create additional write scopes, you need to use the Exchange Management Shell. After you create the write scope, you can apply it to the roles on the role group using the **Write scope** field. For more information about creating write scopes, see [Create a Regular or Exclusive Scope](http://technet.microsoft.com/library/b97a5be3-15cc-4954-ba30-a824a95e21be.aspx).
  
    
    


