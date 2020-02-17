---
title: 'İzlenecek yol: Kod Kusurları için C/C++ Kodunu Analiz Etme'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- C/C++, code analysis
- code analysis, walkthroughs
- code, analyzing C/C++
- code analysis tool, walkthroughs
author: corob-msft
ms.author: corob
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 74a878b8c64955927357e45c668c4d100007d373
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/15/2020
ms.locfileid: "77271816"
---
# <a name="walkthrough-analyzing-cc-code-for-defects"></a>İzlenecek yol: Kod Kusurları için C/C++ Kodunu Analiz Etme

Bu izlenecek yol, C/C++ C++ Code için kod analizi aracını kullanarak olası kod kusurları için c/Code 'un nasıl çözümlendiğini gösterir.

- Yerel kodda Kod analizini Çalıştır.
- Kod hatası uyarılarını çözümleyin.
- Uyarıyı hata olarak değerlendirin.
- Kod hatası analizini geliştirmek için kaynak koda not ekleyin.

## <a name="prerequisites"></a>Önkoşullar

- [Demo örneğinin](../code-quality/demo-sample.md)bir kopyası.
- C/C++hakkında temel bilgiler.

### <a name="to-run-code-defect-analysis-on-native-code"></a>Yerel kodda kod hatası analizini çalıştırmak için

1. Tanıtım çözümünü [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]açın.

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

     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]' de seçtiğiniz geliştirici profiline bağlı olarak, **Görünüm** menüsünde **diğer pencereler** ' i işaret etmeniz ve ardından **hata listesi**' e tıklamanız gerekebilir.

2. **Hata listesi**, aşağıdaki uyarıya çift tıklayın:

     Uyarı C6230: anlamsal olarak farklı türler arasında örtük atama: Boole bağlamında HRESULT kullanılıyor.

     Kod Düzenleyicisi, `bool ProcessDomain()`işlevindeki uyarıya neden olan satırı görüntüler. Bu uyarı, bir `HRESULT` Boole sonucunun beklenen bir ' if ' ifadesinde kullanıldığını gösterir.  Bu genellikle bir hata olur çünkü `S_OK` HRESULT, It işlevinden döndürüldüğünde, başarılı olduğunu gösterir, ancak `false`olarak değerlendirilen bir Boole değerine dönüştürülür.

3. Bu uyarıyı, bir `HRESULT` dönüş değeri başarıyı gösteriyorsa `true` dönüştürür `SUCCEEDED` makrosunu kullanarak düzeltin. Kodunuz aşağıdaki koda benzemelidir:

   ```cpp
   if (SUCCEEDED (ReadUserAccount()) )
   ```

4. **Hata listesi**, aşağıdaki uyarıya çift tıklayın:

     Uyarı C6282: yanlış işleç: test bağlamında sabite atama. Was = = amaçlıdır mi?

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

   ```cpp
   if (nullptr != newNode)
   {
       newNode->data = value;
       newNode->next = 0;
       node->next = newNode;
   }
   ```

9. Ek açıklama projesini yeniden derleyin.

     Proje herhangi bir uyarı veya hata olmadan oluşturulur.

### <a name="to-use-source-code-annotation"></a>Kaynak kodu ek açıklamasını kullanmak için

1. İşaretçi değerlerinin null olabileceğini göstermek için `AddTail` biçimsel parametrelere ve dönüş değerine açıklama ekleyin:

   ```cpp
   _Ret_maybenull_ LinkedList* AddTail(_Maybenull_ LinkedList* node, int value)
   ```

2. Ek açıklama projesini yeniden derleyin.

3. **Hata listesi**, aşağıdaki uyarıya çift tıklayın:

     Uyarı C6011: ' node ' NULL işaretçisinin başvurusunu kaldırma.

     Bu uyarı, işleve geçirilen düğümün null olabileceğini ve uyarının oluşturulduğu satır numarasını belirtir.

4. Bu uyarıyı düzeltmek için, geçirilen değeri sınamak üzere işlevin başındaki bir ' if ' ifadesini kullanın. Kodunuz aşağıdaki koda benzemelidir:

   ```cpp
   if (nullptr == node)
   {
        return nullptr;
   }
   ```

5. Ek açıklama projesini yeniden derleyin.

     Proje artık herhangi bir uyarı veya hata olmadan oluşturulur.

## <a name="see-also"></a>Ayrıca bkz.

[Izlenecek yol: kod kusurları Için yönetilen kodu analiz](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)
, [C/C++ için kod analizi](../code-quality/code-analysis-for-c-cpp-overview.md)
