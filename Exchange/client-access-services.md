---
title: Client Access services
ms.prod: EXCHANGE
ms.assetid: 87e206ab-7a7b-4b4f-be1a-5035713c74d2
---


# Client Access services
Overview of the Client Access services on Mailbox servers in Exchange 2016
In Exchange Server 2016, the Client Access services on Mailbox servers provide authentication and proxy services for internal and external client connections. The Client Access services are stateless, so data isn't queued or stored in them. In Exchange 2016, the Client Access services are part of the Mailbox server, so you can't configure a standalone Client Access server like you could in previous versions of Exchange. For more information, see  [Client access protocol architecture](exchange-2016-architecture.md#ClientAccessProtocol).
  
    
    

Client connectivity in Exchange 2016 is similar to Exchange 2013, but different from Exchange 2010:
- Outlook clients use MAPI over HTTP or Outlook Anywhere (RPC over HTTP). In Exchange 2016, MAPI over HTTP is enabled by default.
    
  
- Exchange 2016 requires fewer namespaces for site-resilient solutions than Exchange 2010. For more information, see  [Namespace Planning in Exchange 2016](https://blogs.technet.com/b/exchange/archive/2015/10/06/namespace-planning-in-exchange-2016.aspx).
    
  

## Client Access services functionality

The Client Access services in Exchange 2016 function much like a front door, admitting all client connection requests and routing them to the correct mailbox database. The Client Access services provide network security such as Transport Layer Security (TLS) encryption, and manage client connections through redirection and proxying. The Client Access services authenticate client connections and typically proxy the connection request to the Mailbox server that holds the active copy of the user's mailbox. In some cases, the Client Access services might redirect the request to the Client Access services on another Exchange server, either in a different location or on a more recent version of Exchange.
  
    
    
The Client Access services have the following features:
  
    
    

- **Stateless services** In previous versions of Exchange, many of the Client Access protocols required session affinity. For example, Outlook Web App in Exchange 2010 required that all requests from a particular client be handled by a specific Client Access server within a load balanced array of Client Access servers. In Exchange 2016, the Client Access services are stateless. In other words, because all processing for the mailbox happens in the backend services on the Mailbox server, it doesn't matter which instance of the Client Access service in an array of Client Access services receives each individual client request. This means that session affinity is no longer required at the load balancer level. This allows inbound connections to Client Access services to be balanced by using simple load balancing techniques such as DNS round-robin. It also allows hardware load balancing devices to support significantly more concurrent connections. For more information, see [Load Balancing in Exchange 2016](https://blogs.technet.com/b/exchange/archive/2015/10/08/load-balancing-in-exchange-2016.aspx).
    
  
- **Connection pooling** The Client Access services handle client authentication and send the **AuthN** data to the backend services on the Mailbox server. The account that's used by the Client Access services to connect to the backend services on Mailbox servers is a privileged account that's a member of the Exchange Servers group. This allows the Client Access services to pool connections to the backend services on Mailbox servers effectively. An array of Client Access services can handle millions of client connections from the Internet, but far fewer connections are used to proxy the requests to the backend services on Mailbox servers than in Exchange 2010. This improves processing efficiency and end-to-end latency.
    
  

> [!NOTE]
> Don't confuse an array of Client Access services with an RPC Client Access Server array that was used for RPC over TCP client connections in Exchange 2010. In Exchange 2016, an array of Client Access services simply indicates a group of load-balanced Client Access services on Exchange 2016 servers. 
  
    
    


## Management tasks in the Client Access services


- **Digital certificates** Although Exchange 2016 uses self-signed certificates to encrypt and authenticate connections between Exchange servers, you need to install and configure certificates to encrypt client connections. For more information, see [Digital certificates and encryption in Exchange 2016](digital-certificates-and-encryption-in-exchange-2016.md).
    
  
- **Kerberos authentication for load-balanced Client Access services** For more information, see [Configuring Kerberos authentication for load-balanced Client Access services](configuring-kerberos-authentication-for-load-balanced-client-access-services.md).
    
  

