---
title: Eski dil hizmetlerinde Gezinti çubuğu desteği
description: Eski dil hizmetlerinde Gezinti Çubuğunu nasıl destekleyebilirsiniz? Düzenleyici görünümündeki Gezinti çubuğu, dosyanın türlerini ve üyelerini görüntüler.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Navigation bar, supporting in language services [managed package framework]
- language services [managed package framework], Navigation bar
ms.assetid: 2d301ee6-4523-4b82-aedb-be43f352978e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: d858d698339a5598765daf151af745ce8e2414607f791a0b0e1c7ac121c53832
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121432039"
---
# <a name="support-for-the-navigation-bar-in-a-legacy-language-service"></a>Eski Dil Hizmetinde Gezinti Çubuğu için Destek
Düzenleyici görünümünün üst kısmında yer alan Gezinti çubuğu, dosyanın türlerini ve üyelerini görüntüler. Türler sol açılan listesinde, üyeler ise sağ açılan listesinde gösterilir. Kullanıcı bir tür seçerken, caret türün ilk satırına yerleştirilir. Kullanıcı bir üyeyi seçerken, caret üyenin tanımına yerleştirilir. Açılan kutular, caret'in geçerli konumunu yansıtacak şekilde güncelleştirilir.

## <a name="displaying-and-updating-the-navigation-bar"></a>Gezinti çubuğunu Görüntüleme ve Güncelleştirme
 Gezinti çubuğunu desteklemek için sınıfından bir sınıf türetmeli ve <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> yöntemini <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> uygulamalısiniz. Dil hizmetinize bir kod penceresi ver verili olduğunda temel sınıf, kod <xref:Microsoft.VisualStudio.Package.LanguageService> penceresini temsil eden nesneyi içeren örneğini <xref:Microsoft.VisualStudio.Package.CodeWindowManager> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> oluşturur. Ardından <xref:Microsoft.VisualStudio.Package.CodeWindowManager> nesnesine yeni bir nesne <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> verilir. yöntemi <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> bir nesnesi <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> alır. Sınıf örneğinizi geri dönersiniz, iç listeleri doldurmak için yönteminizi çağırarak ve nesnenizi <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> <xref:Microsoft.VisualStudio.Package.CodeWindowManager> açılan çubuk <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] yöneticisine iletir. Açılan çubuk yöneticisi de iki açılan çubuğu tutan nesneyi kurmak <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.SetDropdownBar%2A> <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> için <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar> nesnenizin yöntemini çağırarak.

 Caret hareket ettiğinde yöntemi <xref:Microsoft.VisualStudio.Package.LanguageService.OnIdle%2A> yöntemini <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> çağrılır. Temel <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> yöntem, Gezinti <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> çubuğunun <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> durumunu güncelleştirmek için sınıfınıza yöntemini çağrır. Bu yönteme bir <xref:Microsoft.VisualStudio.Package.DropDownMember> nesne kümesi iletirsiniz. Her nesne, açılan liste içinde bir girdiyi temsil eder.

## <a name="the-contents-of-the-navigation-bar"></a>Gezinti Çubuğunun İçeriği
 Gezinti çubuğu genellikle türlerin bir listesini ve üye listesini içerir. Türlerin listesi, geçerli kaynak dosyada bulunan tüm türleri içerir. Tür adları tam ad alanı bilgilerini içerir. Aşağıda, iki türE sahip bir C# kodu örneği ve ardından ve bir örnek ve ardından ve bir C# kodu ve daha fazla bilgi ve daha fazla bilgi ve daha fazla C# kodu ve daha fazla C

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

 Tür listesi ve `TestLanguagePackage.TestLanguageService` `TestLanguagePackage.TestLanguageService.Tokens` görüntülenir.

 Üyeler listesi, türler listesinde seçilen türün kullanılabilir üyelerini görüntüler. Yukarıdaki kod örneğini kullanarak, seçilen tür ise, üyeler `TestLanguagePackage.TestLanguageService` listesi ve özel `tokens` üyelerini `serviceName` içerir. İç yapı `Token` görüntülenmez.

 Bir üyenin adını, caret içine yerleştirilirken kalın yapmak için üyeler listesini gerçekleştirebilirsiniz. Üyeler ayrıca gri metinlerde de görüntülenebilir ve bu da, yazıtların şu anda bulunduğu kapsam içinde olmadığını belirtir.

## <a name="enabling-support-for-the-navigation-bar"></a>Gezinti Çubuğu için Desteği Etkinleştirme
 Gezinti çubuğu desteğini etkinleştirmek için özniteliğinin `ShowDropdownBarOption` parametresini olarak <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> ayarlayabilirsiniz. `true` Bu parametre özelliği <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A> ayarlar. Gezinti çubuğunu desteklemek için sınıfındaki <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> yönteminde <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> nesnesini <xref:Microsoft.VisualStudio.Package.LanguageService> uygulamalısiniz.

 yöntemi uygulamanıza <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> özelliği olarak <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A> ayarlanırsa `true` bir nesnesi <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> getirebilirsiniz. Nesneyi geri getire dönersiniz, Gezinti çubuğu görüntülenmez.

 Gezinti çubuğunu gösterme seçeneği kullanıcı tarafından ayarlansa da düzenleyici görünümü açıkken bu denetimin sıfırlanabilir. Değişiklik öncesinde kullanıcının düzenleyici penceresini kapatıp yeniden açması gerekir.

## <a name="implementing-support-for-the-navigation-bar"></a>Gezinti Çubuğu için Destek Uygulama
 yöntemi iki liste (her açılan liste için bir tane) ve her <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> bir listede geçerli seçimi temsil eden iki değer alır. Listeler ve seçim değerleri güncelleştirilebilir; bu durumda yöntemin listelerin değiştiğini <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> belirtmek için geri dönmesi `true` gerekir.

 Türler açılan listesinde seçim değiştikça, üyeler listesinin yeni türü yansıtacak şekilde güncelleştirilmiş olması gerekir. Üyeler listesinde gösterilenler bunlardan biri olabilir:

- Geçerli tür için üye listesi.

- Kaynak dosyada kullanılabilen tüm üyeler, ancak geçerli türde olmayan tüm üyeler gri renkte görüntülenir. Kullanıcı gri renkli üyeleri seçerek hızlı gezinti için kullanılabilir, ancak renk o anda seçili olan türün parçası olmadığını gösterir.

  yönteminin bir <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> uygulaması genellikle aşağıdaki adımları gerçekleştirir:

1. Kaynak dosya için geçerli bildirimlerin listesini al.

     Listeleri doldurmak için çeşitli yollar vardır. Yaklaşımlardan biri, sınıf sürümünüz üzerinde yöntemini çağıran ve tüm bildirimlerin listesini döndüren özel bir ayrıştırma nedeni olan özel <xref:Microsoft.VisualStudio.Package.LanguageService> <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> bir yöntem oluşturmaktır. Başka bir yaklaşım, yöntemi doğrudan <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> yönteminden özel <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> ayrıştırma nedeni ile çağırma olabilir. Üçüncü bir yaklaşım, sınıfındaki son tam ayrıştırma işlemi tarafından döndürülen sınıfındaki bildirimleri önbelleğe almak ve bunu <xref:Microsoft.VisualStudio.Package.AuthoringScope> <xref:Microsoft.VisualStudio.Package.LanguageService> yönteminden almak <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> olabilir.

2. Tür listesini doldurmak veya güncelleştirmek.

     Türler listesinin içeriği, kaynak değiştirdiğinde veya türlerin metin stillerini geçerli caret konumunu temel alarak değiştirmeyi seçtiyebilirsiniz. Bu konumun yöntemine geçir olduğunu <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> unutmayın.

3. Geçerli dikkat imtiyaz konumunu temel alarak türler listesinde seçecek türü belirleme.

     Geçerli caret konumunu kapsayan türü bulmak için adım 1'de elde edilen bildirimleri arayabilir ve ardından türler listesine dizinini belirlemek için türler listesinde aramaabilirsiniz.

4. Seçilen türe göre üye listesini doldurmak veya güncelleştirmek.

     Üyeler listesi, Üyeler açılan listesinde şu anda **görüntülenenleri** yansıtıyor. Kaynak değiştiyse veya yalnızca seçili türün üyelerini görüntüleniyorsanız ve seçili tür değiştiyse, üye listesinin içeriğinin güncelleştirilmiş olması gerekir. Kaynak dosyada tüm üyeleri görüntülemeyi seçerseniz, o anda seçili tür değiştiyse, listede her üyenin metin stili güncelleştirilmiş olması gerekir.

5. Geçerli dikkat imtiyaz konumunu temel alarak üyeler listesinde seçecek üyeyi belirleme.

     1. adımda elde edilen bildirimleri, geçerli caret konumunu içeren üye için aranın ve ardından üye listesine dizinini belirlemek için üye listesinde bu üyeyi arayın.

6. Listelerde `true` veya listelerde herhangi bir değişiklik yapılmışsa geri döner.
