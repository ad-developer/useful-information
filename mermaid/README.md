# JavaScript based diagramming and charting tool that renders Markdown-inspired text definitions to create and modify diagrams dynamically.

**Reference** https://mermaid.js.org/

## Fllowchar diagram 
```mermaid
graph TD;
    A-->B;
    A-->C;
    B-->D;
    C-->D;
```

## Sequence diagram
```mermaid
sequenceDiagram
    participant Alice
    participant Bob
    Alice->>John: Hello John, how are you?
    loop HealthCheck
        John->>John: Fight against hypochondria
    end
    Note right of John: Rational thoughts <br/>prevail!
    John-->>Alice: Great!
    John->>Bob: How about you?
    Bob-->>John: Jolly good!
```

## Class diagram
```mermaid
classDiagram
Class01 <|-- AveryLongClass : Cool
Class03 *-- Class04
Class05 o-- Class06
Class07 .. Class08
Class09 --> C2 : Where am i?
Class09 --* C3
Class09 --|> Class07
Class07 : equals()
Class07 : Object[] elementData
Class01 : size()
Class01 : int chimp
Class01 : int gorilla
Class08 <--> C2: Cool label

```

## Entity Relationship diagram 
```mermaid
erDiagram
    CUSTOMER ||--o{ ORDER : places
    ORDER ||--|{ LINE-ITEM : contains
    CUSTOMER }|..|{ DELIVERY-ADDRESS : uses
```

## C4 Diagram 

```mermaid
flowchart TB

subgraph singlePageApplication[Single Page Application]
    direction LR
    h3[Container: JavaScript and Angular]:::type
    d3[Provides all of the Internet banking\nfuctionality to customers via their\nweb browser]:::description
end
singlePageApplication:::internalContainer

subgraph mobileApp[Mobile App]
    direction LR
    h4[Container: Xamarin]:::type
    d4[Provides a limited subset of the\nInternet banking functionality to\ncustomers via their mobile device]:::description
end
mobileApp:::internalContainer

subgraph database[Database]
    direction LR
    h6[Container: Oracle Database Schema]:::type
    d6[Stores user registration information, \n hashed authentication credentials, \n access logs, etc]:::description
end
database:::internalContainer

subgraph mainframeBankingSystem[Mainfram Banking System]
    h98[-Software System-]:::type
    d98[Stores all of the core banking \n information about customers, \n accounts, transactions etc]:::description
end
mainframeBankingSystem:::externalSystem

subgraph emailSystem[Email System]
    h99[-Software System-]:::type
    d99[The internal Microsoft Exchange \n email system]:::description
end
emailSystem:::externalSystem

singlePageApplication--Make API calls to-->signInController
singlePageApplication--Make API calls to-->resetPasswordController
singlePageApplication--Make API calls to-->accountsSummaryController
mobileApp--Make API calls to-->signInController
mobileApp--Make API calls to-->resetPasswordController
mobileApp--Make API calls to-->accountsSummaryController

subgraph apiApplication[API Application]
    subgraph signInController[Sign In Controller]
        direction LR
        h10[Component: Spring MVC Rest Controller]:::type
        d10[Allows users to sign in to the Internet \n Banking System]:::description
    end
    signInController:::internalComponent

    subgraph resetPasswordController[Reset Password Controller]
        direction LR
        h20[Component: Spring MVC Rest Controller]:::type
        d20[Allows users to reset their passwords \n with a single use URL]:::description
    end
    resetPasswordController:::internalComponent

    subgraph accountsSummaryController[Accounts Summary Controller]
        direction LR
        h30[Component: Spring MVC Rest Controller]:::type
        d30[Provides customers with a summary \n of their bank accounts]:::description
    end
    accountsSummaryController:::internalComponent

    subgraph securityComponent[Security Component]
        direction LR
        h40[Component: Spring Bean]:::type
        d40[Provides functionality related to \n signing in, changing passwords, etc]:::description
    end
    securityComponent:::internalComponent

    subgraph emailComponent[Email Component]
        direction LR
        h50[Component: Spring Bean]:::type
        d50[Sends emails to users]:::description
    end
    emailComponent:::internalComponent

    subgraph mainframeBankingSystemFacade[Mainframe Banking System Facade]
        direction LR
        h60[Component: Spring Bean]:::type
        d60[A facade onto the mainframe \n banking system]:::description
    end
    mainframeBankingSystemFacade:::internalComponent

    signInController--Uses-->securityComponent
    resetPasswordController--Uses-->securityComponent
    resetPasswordController--Uses-->emailComponent
    accountsSummaryController--Uses-->mainframeBankingSystemFacade
end

securityComponent--Reads from and \n writes to-->database
emailComponent--Sends email using-->emailSystem
mainframeBankingSystemFacade--Uses-->mainframeBankingSystem

%% Element type definitions

classDef person fill:#08427b
classDef internalContainer fill:#1168bd
classDef internalComponent fill:#4b9bea
classDef externalSystem fill:#999999

classDef type stroke-width:0px, color:#fff, fill:transparent, font-size:12px
classDef description stroke-width:0px, color:#fff, fill:transparent, font-size:13px
```