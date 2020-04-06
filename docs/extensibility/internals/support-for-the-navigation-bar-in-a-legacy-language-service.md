---
title: Eski Dil Hizmetinde Gezinti Çubuğu desteği | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Navigation bar, supporting in language services [managed package framework]
- language services [managed package framework], Navigation bar
ms.assetid: 2d301ee6-4523-4b82-aedb-be43f352978e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f86dabb0594b1e33c45808efb387fcbe313e3de3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704856"
---
# <a name="support-for-the-navigation-bar-in-a-legacy-language-service"></a>Eski Dil Hizmetinde Gezinti Çubuğu için Destek
Düzenleyici görünümünün üst kısmındaki Gezinti çubuğu dosyadaki türleri ve üyeleri görüntüler. Türler sol açılır açılır da, üyeler sağ açılır da gösterilir. Kullanıcı bir tür seçtiğinde, bakıcı türün ilk satırına yerleştirilir. Kullanıcı bir üye seçtiğinde, bakıcı üyenin tanımına yerleştirilir. Açılan kutular, bakımın geçerli konumunu yansıtacak şekilde güncelleştirilir.

## <a name="displaying-and-updating-the-navigation-bar"></a>Gezinti çubuğunu görüntüleme ve güncelleme
 Gezinti çubuğunu desteklemek için sınıftan <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> bir sınıf türetmeniz ve <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> yöntemi uygulamanız gerekir. Dil hizmetinize bir kod penceresi verildiğinde, taban <xref:Microsoft.VisualStudio.Package.LanguageService> sınıf, <xref:Microsoft.VisualStudio.Package.CodeWindowManager>kod penceresini <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> temsil eden nesneyi içeren , anlık olarak Nesne <xref:Microsoft.VisualStudio.Package.CodeWindowManager> daha sonra yeni <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> bir nesne verilir. <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> Yöntem bir <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> nesne alır. Sınıfınızın <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> bir örneğini döndürecekseniz, iç listeleri doldurmak için metodunuzu <xref:Microsoft.VisualStudio.Package.CodeWindowManager> <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> çağırır ve nesnenizi <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] açılır çubuk yöneticisine geçirir. Açılan çubuk yöneticisi, sırayla, iki <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.SetDropdownBar%2A> açılır <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> çubuğu tutan <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar> nesneyi oluşturmak için nesnenizdeki yöntemi çağırır.

 Caret hareket ettiğinde, <xref:Microsoft.VisualStudio.Package.LanguageService.OnIdle%2A> yöntem <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> yöntemi çağırır. Temel <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> yöntem, <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> Gezinti çubuğunun durumunu güncelleştirmek için sınıfınızdaki <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> yöntemi çağırır. Bu yönteme <xref:Microsoft.VisualStudio.Package.DropDownMember> bir nesne kümesi geçersiniz. Her nesne açılır bir girişi temsil eder.

## <a name="the-contents-of-the-navigation-bar"></a>Gezinti Çubuğu'nun İçeriği
 Gezinti çubuğu genellikle bir tür listesi ve üye listesi içerir. Türlerin listesi, geçerli kaynak dosyada bulunan tüm türleri içerir. Tür adları tam ad alanı bilgilerini içerir. Aşağıda iki türü olan C# kodu örneği verilmiştir:

```csharp
namespace TestLanguagePackage
{
    public class TestLanguageService
    {
        internal struct Token
        {
            int tokenID;
        }
        private Tokens[] tokens;
        private string serviceName;
    }
}
```

 Tür listesi görüntülenir `TestLanguagePackage.TestLanguageService` `TestLanguagePackage.TestLanguageService.Tokens`ve .

 Üyeler listesi, türler listesinde seçilen türün kullanılabilir üyelerini görüntüler. Yukarıdaki kod örneğini `TestLanguagePackage.TestLanguageService` kullanarak, seçilen tür ise, üye listesi özel `tokens` `serviceName`üyeleri ve . İç yapı `Token` görüntülenmez.

 Bir üyenin adını kalın yapmak için üye listesini uygulayabilirsiniz. Üyeler, bakıcının şu anda konumlandırıldığı kapsamda olmadıklarını belirten gri renkte metin olarak da görüntülenebilir.

## <a name="enabling-support-for-the-navigation-bar"></a>Gezinti Çubuğu için Desteği Etkinleştirme
 Gezinti çubuğu için desteği etkinleştirmek için `ShowDropdownBarOption` `true`özniteliğin <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> parametresini . Bu parametre <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A> özelliği ayarlar. Gezinti çubuğunu desteklemek için, <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> <xref:Microsoft.VisualStudio.Package.LanguageService> sınıfta yöntemde nesne uygulamanız gerekir.

 Yöntemin <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> uygulanmasında, özellik <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A> `true`ayarlanmışsa, bir <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> nesneyi döndürebilirsiniz. Nesneyi döndürmezseniz, Gezinti çubuğu görüntülenmez.

 Gezinti çubuğunu gösterme seçeneği kullanıcı tarafından ayarlanabilir, bu nedenle düzenleyici görünümü açıkken bu denetimin sıfırlanabilmesi mümkündür. Değişiklik gerçekleşmeden önce kullanıcının düzenleyici penceresini kapatıp yeniden açması gerekir.

## <a name="implementing-support-for-the-navigation-bar"></a>Gezinti Çubuğu için Destek Uygulama
 Yöntem, <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> iki liste (her açılır bırakma için bir tane) ve her listedeki geçerli seçimi temsil eden iki değer alır. Listeler ve seçim değerleri güncelleştirilebilir ve <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> bu durumda `true` yöntemin listelerin değiştiğini belirtmek için döndürülmesi gerekir.

 Tür açılır bırakma daki seçim değişiklikleri olarak, üye listesi yeni türü yansıtacak şekilde güncelleştirilmelidir. Üye listesinde gösterilenler aşağıdakilerden biri olabilir:

- Geçerli türe ait üye listesi.

- Tüm üyeler kaynak dosyada kullanılabilir, ancak geçerli türde olmayan tüm üyeler gri-out metin görüntülenir. Kullanıcı gri renkteki üyeleri seçebilir, böylece hızlı gezinme için kullanılabilir, ancak renk şu anda seçili türün bir parçası olmadıklarını gösterir.

  Yöntemin <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> uygulanması genellikle aşağıdaki adımları gerçekleştirir:

1. Kaynak dosya için geçerli bildirimlerin listesini alın.

     Listeleri doldurmanın birkaç yolu vardır. Bir yaklaşım, <xref:Microsoft.VisualStudio.Package.LanguageService> tüm bildirimlerin listesini döndüren özel <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> bir ayrıştırmak nedeni ile yöntemi çağıran sınıfın sürümünde özel bir yöntem oluşturmaktır. Başka bir yaklaşım, <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> yöntemi özel <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> ayrışdırman nedeni ile doğrudan yöntemden aramak olabilir. Üçüncü bir yaklaşım, <xref:Microsoft.VisualStudio.Package.AuthoringScope> <xref:Microsoft.VisualStudio.Package.LanguageService> sınıftaki son tam ayrıştma işlemiyle döndürülen sınıftaki bildirimleri <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> önbelleğe almak ve bunu yöntemden almak olabilir.

2. Türlerin listesini doldurveya güncelleştirin.

     Türlistesinin içeriği, kaynak değiştiğinde veya geçerli bakım konumuna göre türlerin metin stilini değiştirmeyi seçtiyseniz güncelleştirilebilir. Bu konumun <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> yönteme geçirildiğini unutmayın.

3. Geçerli bakım konumuna göre türler listesinde seçilecek türü belirleyin.

     Geçerli caret konumunu içeren türü bulmak için adım 1'de alınan bildirimleri arayabilir ve ardından dizinlerini türlistesine belirlemek için bu türiçin tür ler listesini arayabilirsiniz.

4. Seçilen türe göre üye listesini doldurveya güncelleştirin.

     Üyeler listesi, **Üyeler** açılır listesinde şu anda görüntülenenleri yansıtır. Kaynak değiştiyse veya yalnızca seçili türdeki üyeleri görüntülüyorsanız ve seçili tür değiştiyse, üye listesinin içeriğinin güncellenmesi gerekebilir. Kaynak dosyadaki tüm üyeleri görüntülemeyi seçerseniz, şu anda seçili tür değiştiyse, listedeki her üyenin metin stilinin güncelleştirilmesi gerekir.

5. Geçerli caret konumuna göre üye listesinde seçilecek üyeyi belirleyin.

     Geçerli caret pozisyonunu içeren üye için adım 1'de alınan bildirimleri arayın, ardından üye listesine dizinini belirlemek için o üyenin üye listesini arayın.

6. Listelerde veya her iki listedeki seçimlerde değişiklik yapıldıysa geri döndürün. `true`
