---
title: 'İzlenecek yol: hatalar içinC++ C kodunu çözümleme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- C/C++, code analysis
- code analysis, walkthroughs
- code, analyzing C/C++
- code analysis tool, walkthroughs
ms.assetid: eaee55b8-85fe-47c7-a489-9be0c46ae8af
caps.latest.revision: 37
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: c822dbcc6a1ece2040da22a3442dd584c3926d97
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/15/2020
ms.locfileid: "77272440"
---
# <a name="walkthrough-analyzing-cc-code-for-defects"></a>İzlenecek yol: Kod Kusurları için C/C++ Kodunu Analiz Etme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu izlenecek yol, C/C++ C++ Code için kod analizi aracını kullanarak olası kod kusurları için c/Code 'un nasıl çözümlendiğini gösterir.  
  
 Bu kılavuzda, olası kod kusurları için C/C++ kodunuzu çözümlemek üzere Kod analizini kullanma sürecinde adım adım ilerleyin.  
  
 Aşağıdaki adımları tamamlayacaksınız:  
  
- Yerel kodda Kod analizini Çalıştır.  
  
- Kod hatası uyarılarını çözümleyin.  
  
- Uyarıyı hata olarak değerlendirin.  
  
- Kod hatası analizini geliştirmek için kaynak koda not ekleyin.  
  
## <a name="prerequisites"></a>Önkoşullar  
  
- [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] veya [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)].  
  
- [Demo örneğinin](../code-quality/demo-sample.md)bir kopyası.  
  
- C/C++hakkında temel bilgiler.  
  
### <a name="to-run-code-defect-analysis-on-native-code"></a>Yerel kodda kod hatası analizini çalıştırmak için  
  
1. Tanıtım çözümünü [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]açın.  
  
     Demo çözümü artık **Çözüm Gezgini**doldurur.  
  
2. **Derle** menüsünde **çözümü yeniden derle**' ye tıklayın.  
  
     Çözüm herhangi bir hata veya uyarı olmadan oluşturulur.  
  
3. **Çözüm Gezgini**, codekusurları projesini seçin.  
  
4. **Proje** menüsünde **Özellikler**' e tıklayın.  
  
     **Codekusurları Özellik sayfaları** iletişim kutusu görüntülenir.  
  
5. **Kod Analizi**' ne tıklayın.  
  
6. **Derleme IçinC++ Kod analizini etkinleştir** onay kutusunu tıklatın.  
  
7. Codekusurları projesini yeniden derleyin.  
  
     Kod Analizi uyarıları **hata listesi**görüntülenir.  
  
### <a name="to-analyze-code-defect-warnings"></a>Kod hatası uyarılarını çözümlemek için  
  
1. **Görünüm** menüsünde **hata listesi**' a tıklayın.  
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]' de seçtiğiniz geliştirici profiline bağlı olarak, **Görünüm** menüsünde **diğer pencereler** ' i işaret etmeniz ve ardından **hata listesi**' e tıklamanız gerekebilir.  
  
2. **Hata listesi**, aşağıdaki uyarıya çift tıklayın:  
  
     Uyarı C6230: anlamsal olarak farklı türler arasında örtük atama: Boole bağlamında HRESULT kullanılıyor.  
  
     Kod Düzenleyicisi, `bool``ProcessDomain()`işlevindeki uyarıya neden olan satırı görüntüler. Bu uyarı, Boole sonucunun beklenen bir ' if ' bildiriminde bir HRESULT kullanıldığını gösterir.  
  
3. BAŞARıLı makroyu kullanarak bu uyarıyı düzeltin. Kodunuz aşağıdaki koda benzemelidir:  
  
    ```  
    if (SUCCEEDED (ReadUserAccount()) )  
    ```  
  
4. **Hata listesi**, aşağıdaki uyarıya çift tıklayın:  
  
     Uyarı C6282: yanlış işleç: test bağlamında sabite atama. Was = = amaçlıdır mi?  
  
5. Bu uyarıyı, eşitlik için test ederek düzeltin. Kodunuz aşağıdaki koda benzemelidir:  
  
    ```  
    if ((len == ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))  
    ```  
  
### <a name="to-treat-warning-as-an-error"></a>Uyarıyı hata olarak değerlendirmek için  
  
1. Hata. cpp dosyasında, uyarı C6001 bir hata olarak değerlendirmek için aşağıdaki `#pragma` ifadesini dosyanın başına ekleyin:  
  
    ```  
    #pragma warning (error: 6001)  
    ```  
  
2. Codekusurları projesini yeniden derleyin.  
  
     **Hata listesi**, C6001 artık hata olarak görüntülenir.  
  
3. `i` başlatarak ve 0 ' a `j` **hata listesi** kalan iki C6001 hatasını düzeltin.  
  
4. Codekusurları projesini yeniden derleyin.  
  
     Proje herhangi bir uyarı veya hata olmadan oluşturulur.  
  
### <a name="to-correct-the-source-code-annotation-warnings-in-annotationc"></a>Ek açıklama. c ' de kaynak kodu ek açıklaması uyarılarını düzeltmek için  
  
1. Çözüm Gezgini, ek açıklamalar projesini seçin.  
  
2. **Proje** menüsünde **Özellikler**' e tıklayın.  
  
     **Ek açıklamalar Özellik sayfaları** iletişim kutusu görüntülenir.  
  
3. **Kod Analizi**' ne tıklayın.  
  
4. **Derleme IçinC++ Kod analizini etkinleştir** onay kutusunu seçin.  
  
5. Ek açıklama projesini yeniden derleyin.  
  
6. **Hata listesi**, aşağıdaki uyarıya çift tıklayın:  
  
     Uyarı C6011: ' newNode ' NULL işaretçisinin başvurusunu kaldırma.  
  
     Bu uyarı, çağıran tarafından döndürülen değeri denetlemek için hata olduğunu gösterir. Bu durumda, bir **AllocateNode** çağrısı null değer döndürebilir (AllocateNode için işlev bildirimi için bkz. ek açıklamalar. h üstbilgi dosyası).  
  
7. Ek açıklamalar. cpp dosyasını açın.  
  
8. Bu uyarıyı düzeltmek için, dönüş değerini test etmek için bir ' if ' ifadesini kullanın. Kodunuz aşağıdaki koda benzemelidir:  
  
     `if (NULL != newNode)`  
  
     `{`  
  
     `newNode->data = value;`  
  
     `newNode->next = 0;`  
  
     `node->next = newNode;`  
  
     `}`  
  
9. Ek açıklama projesini yeniden derleyin.  
  
     Proje herhangi bir uyarı veya hata olmadan oluşturulur.  
  
### <a name="to-use-source-code-annotation"></a>Kaynak kodu ek açıklamasını kullanmak için  
  
1. Aşağıdaki örnekte gösterildiği gibi, ön ve post koşullarını kullanarak `AddTail` işlevin biçimsel parametrelerini ve dönüş değerini not edin:  
  
     `[returnvalue:SA_Post (Null=SA_Maybe)] LinkedList* AddTail`  
  
     `(`  
  
     `[SA_Pre(Null=SA_Maybe)] LinkedList* node,`  
  
     `int value`  
  
     `)`  
  
2. Ek açıklama projesini yeniden derleyin.  
  
3. **Hata listesi**, aşağıdaki uyarıya çift tıklayın:  
  
     Uyarı C6011: ' node ' NULL işaretçisinin başvurusunu kaldırma.  
  
     Bu uyarı, işleve geçirilen düğümün null olabileceğini ve uyarının oluşturulduğu satır numarasını belirtir.  
  
4. Bu uyarıyı düzeltmek için, dönüş değerini test etmek için bir ' if ' ifadesini kullanın. Kodunuz aşağıdaki koda benzemelidir:  
  
    ```  
    . . .  
    LinkedList *newNode = NULL;   
    if (NULL == node)  
    {  
         return NULL;  
        . . .  
    }  
    ```  
  
5. Ek açıklama projesini yeniden derleyin.  
  
     Proje herhangi bir uyarı veya hata olmadan oluşturulur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek yol: Kod Kusurları için Yönetilen Kodu Analiz Etme](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)
