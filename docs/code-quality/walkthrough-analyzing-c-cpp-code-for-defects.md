---
title: 'İzlenecek yol: C/C++ Kodunda Hata Olup Olmadığını Analiz Etme'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- C/C++, code analysis
- code analysis, walkthroughs
- code, analyzing C/C++
- code analysis tool, walkthroughs
author: mikeblome
ms.author: mblome
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: bdb99cf487995859b9623f11b3559f1b5e7e3ca7
ms.sourcegitcommit: 535ef05b1e553f0fc66082cd2e0998817eb2a56a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72018345"
---
# <a name="walkthrough-analyzing-cc-code-for-defects"></a>İzlenecek yol: C/C++ Kodunda Hata Olup Olmadığını Analiz Etme

Bu izlenecek yol, C/C++ C++ Code için kod analizi aracını kullanarak olası kod kusurları için c/Code 'un nasıl çözümlendiğini gösterir.

- Yerel kodda Kod analizini Çalıştır.
- Kod hatası uyarılarını çözümleyin.
- Uyarıyı hata olarak değerlendirin.
- Kod hatası analizini geliştirmek için kaynak koda not ekleyin.

## <a name="prerequisites"></a>Önkoşullar

- [Demo örneğinin](../code-quality/demo-sample.md)bir kopyası.
- C/C++hakkında temel bilgiler.

### <a name="to-run-code-defect-analysis-on-native-code"></a>Yerel kodda kod hatası analizini çalıştırmak için

1. Tanıtım çözümünü [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ' da açın.

     Demo çözümü artık **Çözüm Gezgini**doldurur.

2. Üzerinde **derleme** menüsünde tıklatın **çözümü yeniden derle**.

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

     @No__t-0 ' da seçtiğiniz geliştirici profiline bağlı olarak, **Görünüm** menüsünde **diğer pencereleri** işaret etmeniz ve ardından **hata listesi**' e tıklamanız gerekebilir.

2. **Hata listesi**, aşağıdaki uyarıya çift tıklayın:

     Uyarı C6230: Anlamsal olarak farklı türler arasında örtük atama: Boole bağlamında HRESULT kullanılıyor.

     Kod Düzenleyicisi `bool ProcessDomain()` işlevindeki uyarıya neden olan satırı görüntüler. Bu uyarı, Boole sonucunun beklenen bir ' if ' bildiriminde bir HRESULT kullanıldığını gösterir.

3. BAŞARıLı makroyu kullanarak bu uyarıyı düzeltin. Kodunuz aşağıdaki koda benzemelidir:

   ```cpp
   if (SUCCEEDED (ReadUserAccount()) )
   ```

4. **Hata listesi**, aşağıdaki uyarıya çift tıklayın:

     Uyarı C6282: Yanlış işleç: test bağlamında sabit 'e atama. Was = = amaçlıdır mi?

5. Bu uyarıyı, eşitlik için test ederek düzeltin. Kodunuz aşağıdaki koda benzemelidir:

   ```cpp
   if ((len == ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))
   ```

### <a name="to-treat-warning-as-an-error"></a>Uyarıyı hata olarak değerlendirmek için

1. Hata. cpp dosyasında, uyarı C6001 bir hata olarak değerlendirmek için aşağıdaki `#pragma` ifadesini dosyanın başına ekleyin:

   ```cpp
   #pragma warning (error: 6001)
   ```

2. Codekusurları projesini yeniden derleyin.

     **Hata listesi**, C6001 artık hata olarak görüntülenir.

3. @No__t-1 ' i ve `j` ' **hata listesi** başlatarak, kalan iki C6001 hatasını düzeltin.

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

     Uyarı C6011: ' NewNode ' NULL işaretçisine başvuruluyor.

     Bu uyarı, çağıran tarafından döndürülen değeri denetlemek için hata olduğunu gösterir. Bu durumda, bir **AllocateNode** çağrısı null değer döndürebilir (AllocateNode için işlev bildirimi için bkz. ek açıklamalar. h üstbilgi dosyası).

7. Ek açıklamalar. cpp dosyasını açın.

8. Bu uyarıyı düzeltmek için, dönüş değerini test etmek için bir ' if ' ifadesini kullanın. Kodunuz aşağıdaki koda benzemelidir:

   ```cpp
   if (NULL != newNode)
   {
   newNode->data = value;
   newNode->next = 0;
   node->next = newNode;
   }
   ```

9. Ek açıklama projesini yeniden derleyin.

     Proje herhangi bir uyarı veya hata olmadan oluşturulur.

### <a name="to-use-source-code-annotation"></a>Kaynak kodu ek açıklamasını kullanmak için

1. Aşağıdaki örnekte gösterildiği gibi, ön ve post koşullarını kullanarak `AddTail` işlevinin biçimsel parametrelerini ve dönüş değerini not edin:

   ```cpp
   [returnvalue:SA_Post (Null=SA_Maybe)] LinkedList* AddTail
   (
   [SA_Pre(Null=SA_Maybe)] LinkedList* node,
   int value
   )
   ```

2. Ek açıklama projesini yeniden derleyin.

3. **Hata listesi**, aşağıdaki uyarıya çift tıklayın:

     Uyarı C6011: ' Node ' NULL işaretçisine başvuruluyor.

     Bu uyarı, işleve geçirilen düğümün null olabileceğini ve uyarının oluşturulduğu satır numarasını belirtir.

4. Bu uyarıyı düzeltmek için, dönüş değerini test etmek için bir ' if ' ifadesini kullanın. Kodunuz aşağıdaki koda benzemelidir:

   ```cpp
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

## <a name="see-also"></a>Ayrıca bkz.

[İzlenecek yol: Kod kusurları için yönetilen kodu analiz etme @ no__t-0 @ no__t-1 ve[CC++ için kod analizi](../code-quality/code-analysis-for-c-cpp-overview.md)
