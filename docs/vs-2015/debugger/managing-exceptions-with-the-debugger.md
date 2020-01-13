---
title: Hata ayıklayıcı ile özel durumları yönetme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.exceptions
- vs.debug.exceptions.find
dev_langs:
- FSharp
- VB
- CSharp
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
caps.latest.revision: 40
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 45b681b8d146fcc4ca8b056cd94bb0ef65cae826
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/13/2020
ms.locfileid: "75918951"
---
# <a name="managing-exceptions-with-the-debugger"></a>Özel Durumları Hata Ayıklayıcısı ile Yönetme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir özel durum bir program yürütüldüğü sırada gerçekleşen bir hata durumu göstergesidir. En önemli özel durumlara yanıt veren işleyiciler sağlamanız gerekir, ancak görmek istediğiniz özel durumları bozmak için hata ayıklayıcıyı nasıl ayarlayabileceğinizi bilmeniz önemlidir.  
  
 Bir özel durum oluştuğunda, hata ayıklayıcı çıkış penceresine bir özel durum iletisi yazar. Aşağıdaki durumlarda yürütme kesintiye uğramayabilir:  
  
- bir özel durum oluştuğunda ve işlenmezse.  
  
- hata ayıklayıcı, herhangi bir işleyici çağrılmadan önce bir özel durum oluştuğunda hemen yürütmeyi kesme olarak ayarlanır.  
  
- [yalnızca kendi kodum](../debugger/just-my-code.md)ayarladıysanız ve hata ayıklayıcı, Kullanıcı kodunda işlenmemiş olan herhangi bir özel durumda kesme olarak ayarlanır.  
  
> [!NOTE]
> ASP.NET hata sayfalarını bir tarayıcıda gösteren bir üst düzey özel durum işleyicisine sahiptir. **Yalnızca kendi kodum** açık olmadığı takdirde yürütmeyi kesintiye uğramaz. Örnek olarak, aşağıdaki [Kullanıcı tarafından işlenmeyen özel durumlarla devam etmek için hata ayıklayıcıyı ayarlama](../debugger/managing-exceptions-with-the-debugger.md#BKMK_UserUnhandled) bölümüne bakın.  
  
> [!NOTE]
> Visual Basic bir uygulamada, hata stili Hata İşleyicilerde kullansanız bile hata ayıklayıcı tüm hataları özel durum olarak yönetir.  
  
## <a name="managing-exceptions-with-the-exception-settings-window"></a>Özel durum ayarları penceresi ile özel durumları yönetme  
 **Özel durum ayarları** penceresini, hangi özel durumların (veya özel durum kümelerinin) hata ayıklayıcının kesintiye neden olacağını ve hangi noktada kesilmesini istediğinizi belirtmek için kullanabilirsiniz. Özel durumlar ekleyebilir veya silebilir veya kesilecek özel durumlar belirtebilirsiniz. Bir çözüm açıkken **hata ayıklama/Windows/özel durum ayarları**' na tıklayarak bu pencereyi açın.  
  
 Özel durumları **özel durum ayarları** araç çubuğunda **Ara** penceresini kullanarak bulabilir veya belirli ad alanlarını filtrelemek için ara 'yı kullanabilirsiniz (örneğin **System.IO**).  
  
### <a name="setting-the-debugger-to-break-when-an-exception-is-thrown"></a>Bir özel durum oluştuğunda hata ayıklayıcıyı bölmek için ayarlama  
 Hata ayıklayıcı, bir özel durumun oluşturulduğu noktada yürütmeyi bölebilir ve bir işleyici çağrılmadan önce özel durumu incelemenize olanak sağlar.  
  
 **Özel durum ayarları** penceresinde, özel durum kategorisi (örneğin, **ortak dil çalışma zamanı özel durumları**, .NET özel durumları) için düğümü genişletin ve bu kategoride belirli bir özel durum için onay kutusunu seçin (örneğin, **System. AccessViolationException**). Bir tüm özel durumlar kategorisi belirleyebilirsiniz.  
  
 ![Denetlenen AccessViolationException](../debugger/media/exceptionsettingscheckaccess.png "ExceptionSettingsCheckAccess")  
  
 Belirli bir özel durumu denetlebiliyorsanız, hata ayıklayıcı yürütmesi, işlenmesinin veya işlenmemiş olmasından bağımsız olarak özel durumun oluşturulduğu her yerde kesilir. Bu noktada, özel durum ilk fırsat özel durumu olarak adlandırılır. Örneğin, birkaç senaryo şunlardır:  
  
1. Aşağıdaki C# konsol uygulamasında Main yöntemi `try/catch` bloğu Içinde bir **AccessViolationException** oluşturur:  
  
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
  
    **Özel durum ayarlarında** **AccessViolationException** işaretliyse, bu kodu hata ayıklayıcıda çalıştırdığınızda yürütme `throw` satırına kesilir. Ardından, yürütme devam edebilirsiniz. Konsol, iki satır görüntülenmesi gerekir:  
  
   ```  
   caught exception  
   goodbye  
   ```  
  
    Ancak `here` satırı görüntülenmez.  
  
2. Bir C# konsol uygulaması, bir özel durum oluşturan ve onu işleyen ve onu işlemeyen ikinci bir yöntem olan iki yöntemi olan bir sınıf içeren bir sınıf kitaplığına başvurur:  
  
   ```vb  
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
  
    Konsol uygulamasının Main () yöntemi aşağıda verilmiştir:  
  
   ```csharp  
   static void Main(string[] args)  
   {  
       Class1 class1 = new Class1();  
       class1.ThrowHandledException();  
       class1.ThrowUnhandledException();  
   }  
   ```  
  
    **Özel durum ayarları**'nda **AccessViolationException** işaretliyse, bu kodu hata ayıklayıcıda çalıştırdığınızda yürütme, hem **ThrowHandledException ()** hem de **ThrowUnhandledException ()** içindeki `throw` satırına kesilir.  
  
   Özel durum ayarlarını varsayılanlara geri yüklemek isterseniz, araç çubuğundaki **geri yükle** düğmesine tıklayabilirsiniz:  
  
   ![Özel durum ayarlarındaki Varsayılanları geri yükleme](../debugger/media/restoredefaultexceptions.png "RestoreDefaultExceptions")  
  
### <a name="BKMK_UserUnhandled"></a>Kullanıcı tarafından işlenmeyen özel durumlarla devam etmek için hata ayıklayıcı ayarlanıyor  
 [Yalnızca kendi kodum](../debugger/just-my-code.md)ile .NET veya JavaScript kodunda hata ayıklaması yapıyorsanız, hata ayıklayıcıya Kullanıcı kodunda işlenmemiş ancak başka bir yerde işlenen özel durumların kesilmesini olmadığını söyleyebilirsiniz.  
  
1. **Özel durum ayarları** penceresinde, pencere ' ye sağ tıklayıp **sütunları göster**' i seçerek bağlam menüsünü açın. ( **Yalnızca kendi kodum**kapalıysa, bu komutu görmezsiniz.)  
  
2. **Ek eylemler**adlı ikinci bir sütun görmeniz gerekir. Bu sütun, belirli özel durumlarda **Kullanıcı kodu tarafından işlenmemiş olduğunda devam eder** , yani bu özel durum Kullanıcı kodunda işlenmediğinde ancak dış kodda işlenirse hata ayıklayıcının kesintiye uğramaması anlamına gelir.  
  
3. Bu ayarı belirli bir özel durum için (özel durum seçin, sağ tıklayın ve **Kullanıcı kodunda yakalandığınızda devam et**/Kaldır ' ı seçin) veya tüm özel durumlar kategorisi için (örneğin, tüm ortak dil çalışma zamanı özel durumları) değiştirebilirsiniz.  
  
   Örneğin, ASP.NET Web uygulamaları özel durumları bir HTTP 500 durum koduna dönüştürerek işler ([ASP.NET API 'de özel durum işleme](/aspnet/web-api/overview/error-handling/exception-handling)) ve özel durumun kaynağını belirlemenize yardımcı olabilir. Aşağıdaki örnekte, kullanıcı kodu çağrıda `String.Format()` oluşturan bir <xref:System.FormatException>. Yürütme aşağıdaki gibi ayırır:  
  
   ![Kullanıcı&#45;tarafından açılmamış özel durum üzerinde kesintiler](../debugger/media/exceptionunhandledbyuser.png "ExceptionUnhandledByUser")  
  
### <a name="adding-and-deleting-exceptions"></a>Özel durum ekleme ve silme  
 Ekleme ve özel durumları silebilirsiniz. Özel durumu seçip, özel durum **ayarları** araç çubuğunda **Sil** düğmesine (eksi işareti) tıklayarak veya özel duruma sağ tıklayıp bağlam menüsünden **Sil** ' i seçerek herhangi bir kategorideki herhangi bir tür özel durumu silebilirsiniz. Bir özel durumun silinmesi, özel durumdan kaldırılmış olarak aynı etkiye sahiptir ve bu, hata ayıklayıcının oluşturulduğu zaman kesintiye uğramaması anlamına gelir.  
  
 Özel durum eklemek için: özel durum **ayarları** penceresinde, özel durum kategorisinden birini seçin (örneğin, **ortak dil çalışma zamanı**) ve **Ekle** düğmesine tıklayın. Özel durumun adını (örneğin,) yazın. **System. UriTemplateMatchException**). Özel durum listeye eklenir (alfabetik sırada) ve otomatik olarak denetlenir.  
  
 GPU bellek erişimi özel durumları, JavaScript çalışma zamanı özel durumları veya Win32 özel durumlar kategorilerine bir özel durum eklemek istiyorsanız, hata kodunu ve açıklamayı da dahil etmeniz gerekir.  
  
> [!TIP]
> İmlanızı kontrol edin! **Özel durum ayarları** penceresi, eklenen bir özel durumun varlığını denetlemez. Bu nedenle, **Sydıtem. UriTemplateMatchException**yazarsanız, bu özel durum için bir giriş alırsınız ( **System. UriTemplateMatchException**için değil).  
  
 Özel durum ayarları çözümün. suo dosyasında kalıcı hale getirilir, bu nedenle belirli bir çözüme uygulanır. Belirli özel durum ayarlarını çözümler genelinde yeniden kullanamazsınız. Bu noktada, yalnızca eklenen özel durumlar kalıcıdır; Silinen özel durumlar değildir. Diğer bir deyişle, bir özel durum ekleyebilir, çözümü kapatıp yeniden açabilirsiniz ve özel durum hala orada olur. Ancak, bir özel durum silin ve çözümü Kapat/yeniden, özel durum yeniden görünür.  
  
 **Özel durum ayarları** penceresi, C# ancak Visual Basic'de genel özel durum türlerini destekler. Özel durumlar gibi kesmek `MyNamespace.GenericException<T>`, özel durum olarak eklemelisiniz **MyNamespace.GenericException'1**. Diğer bir deyişle, şöyle bir özel durum oluşturduysanız:  
  
```csharp  
public class GenericException<T> : Exception  
{  
    public GenericException() : base("This is a generic exception.")  
    {  
    }  
}  
```  
  
 Özel durumu aşağıdaki gibi **özel durum ayarlarına** ekleyebilirsiniz:  
  
 ![Genel özel durum ekleme](../debugger/media/addgenericexception.png "AddGenericException")  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özel durumdan sonra yürütmeye devam](../debugger/continuing-execution-after-an-exception.md) etme   
 [Nasıl yapılır: özel durumdan sonra sistem kodunu inceleme](../debugger/how-to-examine-system-code-after-an-exception.md)   
 [Nasıl yapılır: yerel çalışma zamanı denetimlerini kullanma](../debugger/how-to-use-native-run-time-checks.md)   
 [C çalışma zamanı kitaplığı olmadan çalışma zamanı denetimlerini kullanma](../debugger/using-run-time-checks-without-the-c-run-time-library.md)   
 [Özel durum yardımcısı](https://msdn.microsoft.com/library/992892ac-9d52-44cc-bf09-b44bfc5befeb)   
 [Hata Ayıklayıcısı Temel Bilgileri](../debugger/debugger-basics.md)
