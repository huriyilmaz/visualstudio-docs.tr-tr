---
title: Hata ayıklayıcısı ile özel durumları | Microsoft Docs
description: Hata ayıklayıcının hangi özel durumlarda hata ayıklayıcıda hata ayıklayıcısının kesmesi ve nasıl işlen olduğunu belirtmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 10/09/2018
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 89795df3a4c6b87c6a878cd07a072027f880e660
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390430"
---
# <a name="manage-exceptions-with-the-debugger-in-visual-studio"></a>Hata ayıklayıcısı ile özel durumları Visual Studio

Özel durum, program yürütülürken oluşan hata durumunun göstergesidir. Hata ayıklayıcıya hangi özel durumların veya özel durum kümelerinin üzerinde kesmesi ve hangi noktada hata ayıklayıcının kesmesi (yani hata ayıklayıcıda duraklama) istemesi olduğunu söylemek için kullanabilirsiniz. Hata ayıklayıcısı kırılırsa, özel durumun nerede olduğunu gösterir. Ayrıca özel durumlar ekleyebilir veya silebilirsiniz. Özel Durum Ayarları penceresini açmak Visual Studio için **Windows >** Özel > Ayarları'> hata **ayıklamayı** kullanın.

En önemli özel durumlara yanıt veren işleyiciler sağlama. Özel durumlar için işleyici ekleme hakkında daha fazla şey biliyorsanız bkz. Daha iyi [C# kodu yazarak hataları düzeltme.](../debugger/write-better-code-with-visual-studio.md) Ayrıca, hata ayıklayıcıyı bazı özel durumlar için yürütmeyi her zaman bozacak şekilde yapılandırmayı öğrenin.

Bir özel durum oluştuğunda, hata ayıklayıcı Çıkış penceresine bir özel **durum iletisi** yazar. Aşağıdaki durumlarda yürütmeyi bozan bir durum olabilir:

- Ele olmayan bir özel durum oluşturur.
- Hata ayıklayıcısı, herhangi bir işleyici çağrılmadan önce yürütmeyi bozacak şekilde yapılandırılır.
- hata [ayıklayıcısını Yalnızca kendi kodum](../debugger/just-my-code.md)ve hata ayıklayıcı, kullanıcı kodunda iş gerektirilen özel durumları bozmak üzere yapılandırılmıştır.

> [!NOTE]
> ASP.NET tarayıcıda hata sayfalarını gösteren üst düzey bir özel durum işleyicisi vardır. Bu, açık değilse **Yalnızca kendi kodum** kesmez. Bir örnek için, [aşağıdaki Hata ayıklayıcıya kullanıcı tarafından işlanmamış özel durumlara devam edeceğini söyleme.](#BKMK_UserUnhandled)

<!-- Two consecutive notes are intentional here...-->

> [!NOTE]
> Hata Visual Basic hata işleyicileri kullansanız bile hata ayıklayıcı tüm hataları özel durum olarak yönetir.

## <a name="tell-the-debugger-to-break-when-an-exception-is-thrown"></a>Hata ayıklayıcısına bir özel durum sızıp kesmelerini söyleyin

Hata ayıklayıcısı, yürütmeyi bir özel durumun at olduğu noktada bozarak bir işleyici çağrılmadan önce özel durumu incelersiniz.

Özel Durum **Ayarları penceresinde** ( Hata ayıklama >**Windows >** Özel Durum Ayarları), Ortak Dil Çalışma Zamanı Özel Durumları gibi bir özel durum kategorisi için **düğümü genişletin.** Ardından ilgili kategori içindeki **System.AccessViolationException** gibi belirli bir özel durum için onay kutusunu seçin. Ayrıca bir özel durum kategorisinin tamamını da seçin.

![AccessViolationException denetlendi](../debugger/media/exceptionsettingscheckaccess.png "ExceptionSettingsCheckAccess")

> [!TIP]
> Özel Durum Ayarları araç çubuğundaki Ara  penceresini kullanarak belirli özel durumları bulabilir veya belirli ad alanlarını filtrelemek için arama kullanabilirsiniz (örneğin, **System.IO).** 

Özel Durum Ayarları penceresinde bir **özel durum** seçersiniz, hata ayıklayıcısı yürütmesi, özel durumun iş olup olmadığı fark etmez. Artık özel durum, ilk şans özel durumu olarak an gelir. Örneğin, birkaç senaryo şöyledir:

- Aşağıdaki C# konsol uygulamasında Main yöntemi bir bloğun içinde **bir AccessViolationException** `try/catch` atar.

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

  Özel Durum **Ayarları'nın içinde AccessViolationException'ı** işaretli **yaptısanız,** hata ayıklayıcıda bu kodu çalıştırarak yürütme `throw` satırda kesme olur. Ardından yürütmeye devam edersiniz. Konsolun her iki satırı da görüntülemesi gerekir:

  ```cmd
  caught exception
  goodbye
  ```

  ancak satırı `here` görüntülemez.

- C# konsol uygulaması, iki yöntemi olan bir sınıf kitaplığına başvurur. Bir yöntem bir özel durum oluşturur ve bunu işlerken ikinci yöntem aynı özel durumu oluşturur ancak bunu işlemez.

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

  Konsol uygulamasının Main() yöntemi şöyledir:

  ```csharp
  static void Main(string[] args)
  {
      Class1 class1 = new Class1();
      class1.ThrowHandledException();
      class1.ThrowUnhandledException();
  }
  ```

  Özel Durum **Ayarları'nde AccessViolationException** denetlenirse, hata ayıklayıcıda bu kodu çalıştırarak yürütme hem `throw` **ThrowHandledException()** hem de **ThrowUnhandledException()** satırda kesme olur.

Özel durum ayarlarını varsayılanlara geri yüklemek için Listeyi varsayılan **ayarlara geri yükle düğmesini** seçin:

![Özel Durum Ayarları'nın varsayılanlarını geri yükleme](../debugger/media/restoredefaultexceptions.png "RestoreDefaultExceptions")

## <a name="tell-the-debugger-to-continue-on-user-unhandled-exceptions"></a><a name="BKMK_UserUnhandled"></a>Hata ayıklayıcıya kullanıcı tarafından işlanmamış özel durumlarla devam edeceğini söyleyin

[Yalnızca kendi kodum](../debugger/just-my-code.md)ile .NET veya JavaScript kodunda hata ayıklarsanız, hata ayıklayıcıya kullanıcı kodunda işnilen ancak başka bir yerde işleyen özel durumlar için hata ayıklamayı önlemesini söylersiniz.

1. Özel Durum **Ayarları penceresinde,** bir sütun etiketine sağ tıklayarak kısayol menüsünü açın ve ardından Sütunları Göster'i > **Eylemler'i seçin.** (Bu komutu **Yalnızca kendi kodum,** bu komutu görmeyebilirsiniz.) Ek Eylemler adlı **üçüncü bir sütun** görüntülenir.

   ![Ek Eylemler sütunu](../debugger/media/additionalactionscolumn.png "Adtionalactionscolumn")

   Bu sütundaki **kullanıcı** kodunda işsiz olduğunda Devam'ı gösteren bir özel durum için, bu özel durum kullanıcı kodunda iş değilse ancak harici olarak işlandı ise hata ayıklayıcı devam eder.

2. Belirli bir özel durum için bu ayarı değiştirmek üzere özel durumu seçin, kısayol menüsünü göstermek için sağ tıklayın ve Kullanıcı Kodunda İşlenilen Durumda **Devam'ı seçin.** Ayrıca, tüm Ortak Dil Çalışma Zamanı özel durumları gibi özel durumlar kategorisinin tamamı için ayarı değiştirebilirsiniz.

   ![**Kullanıcı kodunda iş değilken devam** ayarı](../debugger/media/continuewhenunhandledinusercodesetting.png "Devam Whenunhandledınusercodesetting")

Örneğin, ASP.NET uygulamaları özel durumları HTTP 500 durum koduna[(ASP.NET Web](/aspnet/web-api/overview/error-handling/exception-handling)API'sinde özel durum işleme) dönüştürerek özel durumları işlemektedir. Bu, özel durumun kaynağını belirlemenize yardımcı olabilir. Aşağıdaki örnekte, kullanıcı kodu bir yapan çağrısı `String.Format()` <xref:System.FormatException> yapar. Yürütme şu şekilde sonlanıyor:

![İşlenemeyen&#45;kullanıcı üzerinde kesmeler](../debugger/media/exceptionunhandledbyuser.png "ExceptionUnhandledByUser")

## <a name="add-and-delete-exceptions"></a>Özel durumları ekleme ve silme

Özel durumlar ekleyebilir ve silebilirsiniz. Bir kategorideki özel durum türünü silmek için özel  durumu seçin ve Özel Durum Ayarları araç çubuğundaki Listeden seçilen özel durumu sil düğmesini (eksi **işareti)** seçin. Veya özel durumu sağ tıklar ve kısayol **menüsünden Sil'i** seçebilirsiniz. Bir özel durumu silmek, özel durumun işaretinin kaldırmış olmasıyla aynı etkiye sahiptir ve bu da hata ayıklayıcının hata ayıklayıcısının oluşturma sırasında kesmeme durumudur.

Özel durum eklemek için:

1. Özel Durum **Ayarları penceresinde,** özel durum kategorilerinden birini seçin (örneğin, Ortak Dil **Çalışma Zamanı).**

2. Seçili **kategoriye özel durum ekle düğmesini** (artı işareti) seçin.

   ![**Seçili kategoriye özel durum ekle** düğmesi](../debugger/media/addanexceptiontotheselectedcategorybutton.png "AddAnExceptionToTheSelectedCategoryButton")

3. Özel durumun adını yazın (örneğin, **System.UriTemplateMatchException).**

   ![Özel durum adını yazın](../debugger/media/typetheexceptionname.png "TypeTheExceptionName")

   Özel durum listeye eklenir (alfabetik sırada) ve otomatik olarak denetlenir.

GPU Bellek Erişimi Özel Durumları, JavaScript Çalışma Zamanı Özel Durumları veya Win32 Özel Durumları kategorilerine özel durum eklemek için hata kodunu ve açıklamayı ekleyin.

> [!TIP]
> Yazınızı kontrol edin! Özel **Durum Ayarları** penceresi, eklenen bir özel durumun var olup olmadığını denetlemez. Bu **nedenle, Sytem.UriTemplateMatchException** yazarak ilgili özel durum için bir giriş alırsınız **(System.UriTemplateMatchException için değil).**

Özel durum ayarları çözümün .suo dosyasında kalıcıdır, bu nedenle belirli bir çözüme uygulanır. Çözümler arasında belirli özel durum ayarlarını yeniden kullanılamaz. Artık yalnızca eklenen özel durumlar kalıcıdır; silinen özel durumlar değil. Bir özel durum ekleyebilir, çözümü kapatıp yeniden açarak özel durum yine orada olur. Ancak bir özel durumu silebilir ve çözümü kapatır/yeniden açarsanız, özel durum yeniden açılır.

Özel **Durum Ayarları penceresi** C# içinde genel özel durum türlerini destekler, ancak Visual Basic. gibi özel durumları bozmak `MyNamespace.GenericException<T>` için özel durumu **MyNamespace.GenericException'1 olarak eklemeniz gerekir.** Yani, bu kod gibi bir özel durum oluşturduysanız:

```csharp
public class GenericException<T> : Exception
{
    public GenericException() : base("This is a generic exception.")
    {
    }
}
```

Önceki yordamı kullanarak özel durumu **Özel Durum Ayarları'nın** üzerine ebilirsiniz:

![genel özel durum ekleme](../debugger/media/addgenericexception.png "AddGenericException")

## <a name="add-conditions-to-an-exception"></a>Özel durumlara koşullar ekleme

Özel **durumlarda koşulları** ayarlamak için Özel Durum Ayarları penceresini kullanın. Şu anda desteklenen koşullar, özel durum için dahil etmek veya hariç tutmak için modül adlarını içerir. Modül adlarını koşullar olarak ayarerek, özel durum için yalnızca belirli kod modüllerinde kesmeyi seçebilirsiniz. Ayrıca belirli modüllerde bozmayı önlemeyi de seçebilirsiniz.

> [!NOTE]
> Bir özel durum için koşullar ekleme, 'den başlayarak de [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] desteklemektedir.

Koşullu özel durumlar eklemek için:

1. Özel Durum **Ayarları penceresinde** Koşulları düzenle düğmesini seçin veya özel durumu sağ tıklar ve Koşulları **Düzenle'yi seçin.**

   ![Özel durum koşulları](../debugger/media/dbg-conditional-exception.png "DbgConditionalException")

2. Özel duruma ek gerekli koşullar eklemek için her yeni **koşul için Koşul** Ekle'yi seçin. Ek koşul satırları görüntülenir.

   ![Özel durum için ek koşullar](../debugger/media/extraconditionsforanexception.png "ExtraConditionsForAnException")

3. Her koşul satırı için modülün adını yazın ve karşılaştırma işleci listesini **Equals** veya Not **Equals olarak değiştirebilirsiniz.** Birden fazla modül belirtmek için ad içinde joker karakterler ( **\\\*** ) belirtabilirsiniz.

4. Bir koşulu silmeniz gerekirse, koşul **çizgisinin** sonundaki X'i seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Özel durumdan sonra yürütmeye devam etme](../debugger/continuing-execution-after-an-exception.md)<br/>
- [Nasıl yapılır: Özel durumdan sonra sistem kodunu inceleme](../debugger/how-to-examine-system-code-after-an-exception.md)<br/>
- [Nasıl yapılır: Yerel çalışma zamanı denetimlerini kullanma](../debugger/how-to-use-native-run-time-checks.md)<br/>
- [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)
