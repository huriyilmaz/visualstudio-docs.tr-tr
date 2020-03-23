---
title: Hata ayıklama ile özel durumları yönetme | Microsoft Dokümanlar
ms.custom: seodec18
ms.date: 10/09/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.exceptions
- vs.debug.exceptions.find
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- run-time errors
- exception handling, during debugging
- errors [debugger]
- debugger, runtime errors
- On Error-style error handlers
- exceptions, Win32
- run-time errors, debugging
- Win32, exceptions
- run time, exceptions
- error handling
- debugging [Visual Studio], exception handling
- common language runtime, exceptions
- native run-time checks
- exceptions, debugging
ms.assetid: 43a77fa8-37d0-4c98-a334-0134dbca4ece
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 00ad5b41dd0a11661d281f24474b7673ea0a342c
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302156"
---
# <a name="manage-exceptions-with-the-debugger-in-visual-studio"></a>Visual Studio'da hata ayıklamayla ilgili özel durumları yönetme

Özel durum, bir program yürütülürken oluşan bir hata durumunun göstergesidir. Hata ayıklayıcıya hangi özel durumların veya özel durum kümelerinin kırılacağını ve hangi noktada hata ayıklayıcının kırılmasını istediğinizi (diğer bir deyişle hata ayıklayıcıda duraklatma) söyleyebilirsiniz. Hata ayıklama kırıldığında, özel durum nerede atıldığını gösterir. Ayrıca özel durumlar ekleyebilir veya silebilirsiniz. Visual Studio'da açık olan bir çözümle, Özel Durum Ayarları penceresini açmak için **Hata Ayıklama > Windows > Özel Durum** **Ayarları'nı** kullanın.

En önemli özel durumlara yanıt veren işleyiciler sağlayın. Özel durumlar için işleyicileri nasıl ekleyeceğinibilmeniz gerekiyorsa, [daha iyi C# kodu yazarak hataları düzelt'e](../debugger/write-better-code-with-visual-studio.md)bakın. Ayrıca, hata ayıklamanın her zaman bazı özel durumlar için yürütmeyi kıracak şekilde nasıl yapılandırılacağını öğrenin.

Bir özel durum oluştuğunda, hata ayıklama, **Çıktı** penceresine bir özel durum iletisi yazar. Aşağıdaki durumlarda yürütmeyi bozabilir:

- Ele alınamayan bir özel durum atılır.
- Hata ayıklayıcı, herhangi bir işleyici çağrılmadan önce yürütmeyi kesecek şekilde yapılandırılır.
- [Just My Code'u](../debugger/just-my-code.md)ayarladınız ve hata ayıklayıcı kullanıcı kodunda işlenmeyen herhangi bir özel durum için yapılandırılır.

> [!NOTE]
> ASP.NET tarayıcıda hata sayfalarını gösteren üst düzey bir özel durum işleyicisi vardır. **Sadece Kodum** açık olmadığı sürece yürütmeyi bozmaz. Örneğin, aşağıdaki [kullanıcı tarafından işlenmemiş özel durumlara devam etmek için hata ayıklama aracını](#BKMK_UserUnhandled) söyleyin'e bakın.

<!-- Two consecutive notes are intentional here...-->

> [!NOTE]
> Visual Basic uygulamasında hata ayıklayıcı, Hata Stili hata işleyicilerinde kullansanız bile tüm hataları özel durum olarak yönetir.

## <a name="tell-the-debugger-to-break-when-an-exception-is-thrown"></a>Hata ayıklama aracına özel bir özel durum atıldığında kırılmasını söyleyin

Hata ayıklayıcı, özel durum atıldığı noktada yürütmeyi bozabilir, bu nedenle işleyici çağrılmadan önce özel durumu inceleyebilirsiniz.

Özel **Durum Ayarları** penceresinde **(Hata Ayıklama > Windows > Özel Durum Ayarları),** **ortak dil çalışma zamanı özel durumlar**gibi özel durumlar kategorisi için düğümü genişletin. Ardından, bu kategorideki **System.AccessViolationException**gibi belirli bir özel durum için onay kutusunu seçin. Ayrıca, özel durumların tüm kategorisini de seçebilirsiniz.

![Denetlenen AccessViolationException](../debugger/media/exceptionsettingscheckaccess.png "Özel DurumlarAyarlarCheckAccess")

> [!TIP]
> **Özel Durum Ayarları** araç çubuğundaki **Arama** penceresini kullanarak belirli özel durumlar bulabilir veya belirli ad alanlarına **(System.IO**gibi) filtre uygulayacak şekilde aramayı kullanabilirsiniz.

**Özel Durum Ayarları** penceresinde bir özel durum seçerseniz, işlenip işlenmediği ne olursa olsun hata ayıklama yürütmesi özel durum atıldığı her yerde kırılır. Şimdi özel durum ilk şans özel durum olarak adlandırılır. Örneğin, birkaç senaryo aşağıda verilmiştir:

- Aşağıdaki C# konsol uygulamasında, Ana yöntem bir `try/catch` blok içinde **accessviolationexception** atar.

  ```csharp
  static void Main(string[] args)
  {
      try
      {
          throw new AccessViolationException();
          Console.WriteLine("here");
      }
      catch (Exception e)
      {
          Console.WriteLine("caught exception");
      }
      Console.WriteLine("goodbye");
  }
  ```

  **AccessViolationException** **Özel Durum Ayarları'nda**denetlenirse, `throw` hata ayıklayıcıda bu kodu çalıştırdığınızda yürütme satırda bozulur. Daha sonra yürütmedevam edebilirsiniz. Konsol her iki satırı da görüntülemelidir:

  ```cmd
  caught exception
  goodbye
  ```

  ama `here` satırı göstermiyor.

- C# konsolu uygulaması, iki yöntemi olan bir sınıf kitaplığına başvurur. İkinci bir yöntem aynı özel durumu atarken, ancak işlemezken, bir yöntem özel durum atar ve işler.

  ```csharp
  public class Class1
  {
      public void ThrowHandledException()
      {
          try
          {
              throw new AccessViolationException();
          }
          catch (AccessViolationException ave)
          {
              Console.WriteLine("caught exception" + ave.Message);
          }
      }

      public void ThrowUnhandledException()
      {
          throw new AccessViolationException();
      }
  }
  ```

  Konsol uygulamasının Main() yöntemi aşağıda veda edebilirsiniz:

  ```csharp
  static void Main(string[] args)
  {
      Class1 class1 = new Class1();
      class1.ThrowHandledException();
      class1.ThrowUnhandledException();
  }
  ```

  **AccessViolationException** **Özel Durum Ayarları'nda**denetlenirse, `throw` hata ayıklamada bu kodu çalıştırdığınızda hem **ThrowHandledException()** hem de **ThrowUnhandledException()** satırında yürütme bozulur.

Özel durum ayarlarını varsayılanlara geri yüklemek **için, listeyi varsayılan ayarlar düğmesine geri yükle düğmesini** seçin:

![Özel Durum Ayarları'nda varsayılanları geri yükleme](../debugger/media/restoredefaultexceptions.png "Geri YüklemeVarsayılan Özel Durumlar")

## <a name="tell-the-debugger-to-continue-on-user-unhandled-exceptions"></a><a name="BKMK_UserUnhandled"></a>Hata ayıklama aracının kullanıcı tarafından işlenmemiş özel durumlara devam etmesini söyleyin

[.NET](../debugger/just-my-code.md)veya JavaScript kodunu Just My Code ile hata ayıklıyorsanız, hata ayıklayıcıya kullanıcı kodunda işlenmeyen ancak başka bir yerde işlenen özel durumları kırmayı önlemesini söyleyebilirsiniz.

1. Özel **Durum Ayarları** penceresinde, sütun etiketini sağ tıklatarak kısayol menüsünü açın ve ardından **Sütunları > Ek Eylemleri Göster'i**seçin. (Just **My Code'u**kapattıysanız, bu komutu görmezsiniz.) **Ek Eylemler** adlı üçüncü bir sütun görüntülenir.

   ![Ek Eylemler sütunu](../debugger/media/additionalactionscolumn.png "EkEylemlerSütun")

   Bu **sütunda kullanıcı kodunda işlenmediğinde Devam'ı** gösteren bir özel durum için, bu özel durum kullanıcı kodunda işlenmemişse ancak dışarıdan işlenirse hata ayıklayıcı devam ediyor.

2. Belirli bir özel durum için bu ayarı değiştirmek için, özel durum, kısayol menüsünü göstermek için sağ tıklatın ve **Kullanıcı Kodu'nda İşlenmediğinde Devam'ı**seçin. Ayrıca, tüm Ortak Dil Çalışma Zamanı özel durumları gibi tüm özel durumlar kategorisinin ayarını da değiştirebilirsiniz).

   ![**Kullanıcı kodunda işlenmemişken devam et** ayarı](../debugger/media/continuewhenunhandledinusercodesetting.png "ContinueWhenHandledInUserCodeSetting")

Örneğin, ASP.NET web uygulamaları, özel durumun kaynağını belirlemenize yardımcı olmayabilir bir HTTP 500 durum koduna[(ASP.NET Web API'de özel durum işleme)](/aspnet/web-api/overview/error-handling/exception-handling)dönüştürerek özel durumları işler. Aşağıdaki örnekte, kullanıcı kodu bir `String.Format()` . <xref:System.FormatException> Yürütme aşağıdaki gibi tatili:

![Kullanımdan&#45;kullanımsız özel durum üzerinde molalar](../debugger/media/exceptionunhandledbyuser.png "Özel DurumUnhandledByUser")

## <a name="add-and-delete-exceptions"></a>Özel durumlar ekleme ve silme

Özel durumlar ekleyebilir ve silebilirsiniz. Bir kategoriden özel durum türünü silmek için özel durumu seçin ve **Özel Durum Ayarları** araç çubuğundaki liste **düğmesinden (eksi** işareti) seçili özel durumu seçin. Veya özel durumu sağ tıklayıp kısayol menüsünden **Sil'i** seçebilirsiniz. Özel durum silme, özel durum işaretlenmemiş olmasıyla aynı etkiye sahiptir, bu da hata ayıklamanın atıldığında kırılmayatmasıdır.

Özel durum eklemek için:

1. Özel **Durum Ayarları** penceresinde, özel durum kategorilerinden birini seçin (örneğin, **Ortak Dil Çalışma Zamanı).**

2. Seçili kategori düğmesine (artı işareti) **özel durum ekle'yi** seçin.

   ![**Seçili kategoriye özel durum ekleme** düğmesi](../debugger/media/addanexceptiontotheselectedcategorybutton.png "AddanexceptiontoSelectedCategoryButton")

3. Özel durum adını yazın (örneğin, **System.UriTemplateMatchException).**

   ![Özel durum adını yazın](../debugger/media/typetheexceptionname.png "TypeTheExceptionName")

   Özel durum listeye eklenir (alfabetik sırayla) ve otomatik olarak denetlenir.

GPU Bellek Erişim Özel Durumları,JavaScript Çalışma Zamanı Özel Durumlar veya Win32 Özel Durumlar kategorilerine bir özel durum eklemek için hata kodu ve açıklama içerir.

> [!TIP]
> Yazınızı kontrol edin! **Özel Durum Ayarları** penceresi, eklenen bir özel durum olup olmadığını denetlemez. Yani **Sytem.UriTemplateMatchException**yazarsanız, bu özel durum için bir giriş alırsınız (ve **System.UriTemplateMatchException**için değil).

Özel durum ayarları çözümün .suo dosyasında kalıcıdır, bu nedenle belirli bir çözüme uygulanır. Çözümler arasında belirli özel durum ayarlarını yeniden kullanamazsınız. Artık yalnızca eklenen özel durumlar devam ediyor; silinen özel durumlar değildir. Bir özel durum ekleyebilirsiniz, çözümü kapatıp yeniden açabilirsiniz ve özel durum yine de orada olacaktır. Ancak bir özel durumu siler ve çözümü kapatır/yeniden açarsanız, özel durum yeniden görünür.

**Özel Durum Ayarları** penceresi C#'daki genel özel durum türlerini destekler, ancak Visual Basic'te desteklemez. Gibi `MyNamespace.GenericException<T>`özel durumlar kırmak için, **MyNamespace.GenericException'1**olarak özel durum eklemeniz gerekir. Diğer bir şey, bu kod gibi bir özel durum oluşturduysanız:

```csharp
public class GenericException<T> : Exception
{
    public GenericException() : base("This is a generic exception.")
    {
    }
}
```

Önceki yordamı kullanarak **Özel Durum Ayarları'na** özel durum ekleyebilirsiniz:

![genel özel durum ekleme](../debugger/media/addgenericexception.png "AddGenericException")

## <a name="add-conditions-to-an-exception"></a>Özel durum için koşul ekleme

Özel **durumlara** ilişkin koşulları ayarlamak için Özel Durum Ayarları penceresini kullanın. Şu anda desteklenen koşullar, özel durum için dahil etmek veya hariç tutmak için modül adını(lar) içerir. Modül adlarını koşul olarak ayarlayarak, yalnızca belirli kod modüllerinde özel durum için kesmeyi seçebilirsiniz. Ayrıca belirli modülleri kırma önlemek için seçebilirsiniz.

> [!NOTE]
> Bir özel durum için koşullar [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]ekleme' den başlayarak desteklenir.

Koşullu özel durumlar eklemek için:

1. Özel Durum Ayarları penceresindeki **koşulları düzelt** düğmesini seçin veya özel durumu sağ tıklatın ve **Koşulları Edit'i**seçin.

   ![Özel durum koşulları](../debugger/media/dbg-conditional-exception.png "DbgConditionalException")

2. Özel duruma ekstra gerekli koşullar eklemek için, her yeni koşul için **Koşul Ekle'yi** seçin. Ek koşul satırları görüntülenir.

   ![Bir istisna için ek koşullar](../debugger/media/extraconditionsforanexception.png "EkstraKoşullarForanException")

3. Her koşul satırı için modülün adını yazın ve karşılaştırma işleci listesini **Eşitler** veya **Eşit olmayanlarla**değiştirin. Birden fazla modül**\\**belirtmek için adiçinde joker karakterler ( ) belirtebilirsiniz.

4. Bir koşulu silmeniz gerekiyorsa, koşul satırının sonundaki **X'i** seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Özel durumdan sonra yürütmeye devam etme](../debugger/continuing-execution-after-an-exception.md)<br/>
- [Nasıl yapılır: Özel durumdan sonra sistem kodunu inceleme](../debugger/how-to-examine-system-code-after-an-exception.md)<br/>
- [Nasıl yapılır: Yerel çalışma zamanı denetimlerini kullanma](../debugger/how-to-use-native-run-time-checks.md)<br/>
- [C çalışma zamanı kitaplığı olmadan çalışma zamanı denetimlerini kullanma](../debugger/using-run-time-checks-without-the-c-run-time-library.md)<br/>
- [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)
