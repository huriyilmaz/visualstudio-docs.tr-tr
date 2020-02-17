---
title: Tanıtım örneği | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- demo sample [Visual Studio ALM]
- code analysis, samples
ms.assetid: 09e1b9f7-5916-4ed6-a001-5c2d7e710682
caps.latest.revision: 23
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: 3a49859a8cd1c4ffb01f93bf2539fc16c42f8c4c
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/15/2020
ms.locfileid: "77277888"
---
# <a name="demo-sample"></a>Gösterim Örneği
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aşağıdaki yordamlarda Izlenecek yol için örneğin nasıl oluşturulacağı gösterilmektedir [: hatalar Için CC++ /Code çözümleme](../code-quality/walkthrough-analyzing-c-cpp-code-for-defects.md). Şu yordamları oluşturun:  
  
- CppDemo adlı bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] çözümü.  
  
- Codearızaları adlı bir statik kitaplık projesi.  
  
- Ek açıklamalar adlı bir statik kitaplık projesi.  
  
  Yordamlar ayrıca statik kitaplıklar için üst bilgi ve. cpp dosyaları için kod sağlar.  
  
### <a name="create-the-cppdemo-solution-and-the-codedefects-project"></a>CppDemo çözümü ve Codekusurları projesi oluşturma  
  
1. **Dosya** menüsüne tıklayın, **Yeni**' nin üzerine gelin ve ardından **Yeni proje**' ye tıklayın.  
  
2. **Proje türleri** ağaç listesinde, Visual C++ varsayılan diliniz, vs genişletme **diğer dillerde**değilse.  
  
3. **Görsel C++** ' i genişletin ve ardından **genel**' e tıklayın.  
  
4. **Şablonlar**' da **boş proje**' ye tıklayın.  
  
5. **Ad** metin kutusuna **codekusurlarını**yazın.  
  
6. **Çözüm için dizin oluştur** onay kutusunu seçin.  
  
7. **Çözüm adı** metin kutusuna **CppDemo**yazın.  
  
### <a name="configure-the-codedefects-project-as-a-static-library"></a>Codekusurları projesini statik kitaplık olarak yapılandırma  
  
1. Çözüm Gezgini, **Codekusurları** ' na sağ tıklayın ve ardından **Özellikler**' e tıklayın.  
  
2. **Yapılandırma özellikleri** ' ni genişletin ve ardından **genel**' e tıklayın.  
  
3. **Genel** listesinde, **hedef uzantı**' ın yanındaki sütundaki metni seçin ve **. lib**yazın.  
  
4. **Proje Varsayılanları**' nda, **yapılandırma türü**' nün yanındaki sütununa tıklayın ve ardından **statik LIB (. lib)** öğesine tıklayın.  
  
### <a name="add-the-header-and-source-file-to-the-codedefects-project"></a>Üstbilgi ve kaynak dosyayı Codekusurları projesine ekleyin  
  
1. Çözüm Gezgini, **kod hataları**' nı genişletin, **üst bilgi dosyaları**' na sağ tıklayın, **Ekle**' ye ve ardından **Yeni öğe**' ye tıklayın  
  
2. **Yeni öğe Ekle** iletişim kutusunda, **kod**' a ve ardından **üstbilgi dosyası (. h)** ' na tıklayın.  
  
3. **Ad** kutusuna **Bug. cpp** yazın ve ardından **Ekle**' ye tıklayın.  
  
4. Aşağıdaki kodu kopyalayın ve [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] düzenleyicisinde **hata. cpp** dosyasına yapıştırın.  
  
    ```  
    #include <windows.h>  
  
    //    
    //These 3 functions are consumed by the sample  
    //  but are not defined. This project cannot be linked!  
    //  
  
    bool CheckDomain( LPCSTR );  
    HRESULT ReadUserAccount();  
  
    //  
    //These constants define the common sizes of the   
    //  user account information throughout the program  
    //  
  
    const int USER_ACCOUNT_LEN = 256;  
    const int ACCOUNT_DOMAIN_LEN = 128;  
    ```  
  
5. Çözüm Gezgini, **kaynak dosyalar**' a sağ tıklayın, **Yeni**' nin üzerine gelin ve ardından **Yeni öğe**' ye tıklayın.  
  
6. **Yeni öğe Ekle** iletişim kutusunda  **C++ dosya (. cpp)** öğesine tıklayın.  
  
7. **Ad** kutusuna **Bug. cpp** yazın ve ardından **Ekle**' ye tıklayın.  
  
8. Aşağıdaki kodu kopyalayın ve [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] düzenleyicisinde hata. h dosyasına yapıştırın.  
  
    ```  
    #include <stdlib.h>  
    #include "Bug.h"  
  
    // the user account   
    TCHAR g_userAccount[USER_ACCOUNT_LEN] = "";  
    int len = 0;  
  
    bool ProcessDomain()  
    {  
        TCHAR* domain = new TCHAR[ACCOUNT_DOMAIN_LEN];  
        // ReadUserAccount gets a 'domain\user' input from   
        //the user into the global 'g_userAccount'  
        if (ReadUserAccount() )  
        {  
  
            // Copies part of the string prior to the '\'   
            // character onto the 'domain' buffer  
            for( len = 0 ; (len < ACCOUNT_DOMAIN_LEN) && (g_userAccount[len] != '\0') ; len++  )  
            {  
                if ( g_userAccount[len] == '\\' )   
                {  
                    // Stops copying on the domain and user separator ('\')   
                    break;  
                }  
                domain[len] = g_userAccount[len];          
            }  
            if((len= ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))  
            {  
                // '\' was not found. Invalid domain\user string.  
                delete [] domain;  
                return false;  
            }  
            else  
            {  
                domain[len]='\0';  
            }  
            // Process domain string  
            bool result = CheckDomain( domain );  
  
            delete[] domain;  
            return result;  
        }  
        return false;  
    }  
  
    int path_dependent(int n)  
    {  
        int i;  
        int j;  
        if (n == 0)  
            i = 1;  
        else  
            j = 1;  
        return i+j;   
    }  
    ```  
  
9. **Dosya** menüsüne tıklayın ve ardından **Tümünü Kaydet**' e tıklayın.  
  
### <a name="add-the-annotations-project-and-configure-it-as-a-static-library"></a>Ek açıklamalar projesini ekleme ve statik kitaplık olarak yapılandırma  
  
1. Çözüm Gezgini, **CppDemo**' e tıklayın, **Ekle**' nin üzerine gelin ve ardından **Yeni proje**' ye tıklayın.  
  
2. **Yeni Proje Ekle** iletişim kutusunda, görsel C++' i genişletin, **genel**' i ve ardından **boş proje**' yi tıklatın.  
  
3. **Ad** metin kutusuna **ek açıklamalar**yazın ve ardından **Ekle**' ye tıklayın.  
  
4. Çözüm Gezgini, **ek açıklamalar** ' a sağ tıklayın ve ardından **Özellikler**' e tıklayın.  
  
5. **Yapılandırma özellikleri** ' ni genişletin ve ardından **genel**' e tıklayın.  
  
6. **Genel** listesinde, **hedef uzantı**' ın yanındaki sütundaki metni seçin ve **. lib**yazın.  
  
7. **Proje Varsayılanları**' nda, **yapılandırma türü**' nün yanındaki sütununa tıklayın ve ardından **statik LIB (. lib)** öğesine tıklayın.  
  
### <a name="add-the-header-file-and-source-file-to-the-annotations-project"></a>Üst bilgi dosyasını ve kaynak dosyayı ek açıklamalar projesine ekleyin  
  
1. Çözüm Gezgini, **ek açıklamalar**' ı genişletin, **üstbilgi dosyaları**' na sağ tıklayın, **Ekle**' ye ve ardından **Yeni öğe**' ye tıklayın.  
  
2. **Yeni öğe Ekle** Iletişim kutusunda **üst bilgi dosyası (. h)** seçeneğine tıklayın.  
  
3. **Ad** kutusuna, **ek açıklama. h** yazın ve ardından **Ekle**' ye tıklayın.  
  
4. Aşağıdaki kodu kopyalayın ve [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] düzenleyicisinde **ek açıklamalar. h** dosyasına yapıştırın.  
  
    ```  
    #include <CodeAnalysis/SourceAnnotations.h>  
  
    struct LinkedList  
    {  
        struct LinkedList* next;  
        int data;  
    };  
  
    typedef struct LinkedList LinkedList;  
  
    [returnvalue:SA_Post( Null=SA_Maybe )] LinkedList* AllocateNode();  
  
    ```  
  
5. Çözüm Gezgini, **kaynak dosyalar**' a sağ tıklayın, **Yeni**' nin üzerine gelin ve ardından **Yeni öğe**' ye tıklayın.  
  
6. **Yeni öğe Ekle** iletişim kutusunda, **kod** ' a ve ardından  **C++ dosya (. cpp)** ' ye tıklayın.  
  
7. **Ad** kutusuna, **ek açıklama. cpp** yazın ve ardından **Ekle**' ye tıklayın.  
  
8. Aşağıdaki kodu kopyalayın ve [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] düzenleyicisinde **ek açıklamalar. cpp** dosyasına yapıştırın.  
  
    ```  
    #include <CodeAnalysis/SourceAnnotations.h>  
    #include <windows.h>  
    #include <stdlib.h>    
    #include "annotations.h"  
  
    LinkedList* AddTail( LinkedList *node, int value )  
    {  
        LinkedList *newNode = NULL;   
  
        // finds the last node  
        while ( node->next != NULL )   
        {  
            node = node->next;  
        }  
  
        // appends the new node  
        newNode = AllocateNode();   
        newNode->data = value;  
        newNode->next = 0;  
        node->next = newNode;  
  
        return newNode;  
    }  
  
    ```  
  
9. **Dosya** menüsüne tıklayın ve ardından **Tümünü Kaydet**' e tıklayın.
