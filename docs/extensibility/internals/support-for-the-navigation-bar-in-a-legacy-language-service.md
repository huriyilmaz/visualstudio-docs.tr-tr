---
title: Eski dil hizmetinde gezinti çubuğunu destekleme
description: Eski dil hizmetinde gezinti çubuğunu desteklemeyi öğrenin. Düzenleyici görünümündeki gezinti çubuğu, dosyadaki türleri ve üyeleri görüntüler.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Navigation bar, supporting in language services [managed package framework]
- language services [managed package framework], Navigation bar
ms.assetid: 2d301ee6-4523-4b82-aedb-be43f352978e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d33b8452f727037226a50abe6a9493ce132e9564
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99932585"
---
# <a name="support-for-the-navigation-bar-in-a-legacy-language-service"></a>Eski Dil Hizmetinde Gezinti Çubuğu için Destek
Düzenleyici görünümünün en üstündeki gezinti çubuğu, dosyadaki türleri ve üyeleri görüntüler. Türler sol açılır kutuda gösterilir ve Üyeler sağ tarafta gösterilir. Kullanıcı bir tür seçtiğinde, giriş işareti, türün ilk satırına yerleştirilir. Kullanıcı bir üye seçtiğinde, giriş işareti üyenin tanımına yerleştirilir. Açılan kutular, giriş işaretinin geçerli konumunu yansıtacak şekilde güncelleştirilir.

## <a name="displaying-and-updating-the-navigation-bar"></a>Gezinti çubuğunu görüntüleme ve güncelleştirme
 Gezinti çubuğunu desteklemek için, sınıfından bir sınıf türetmeniz <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> ve metodunu uygulamanız gerekir <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> . Dil hizmetinize bir kod penceresi verildiğinde, temel <xref:Microsoft.VisualStudio.Package.LanguageService> sınıf, <xref:Microsoft.VisualStudio.Package.CodeWindowManager> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> kod penceresini temsil eden nesneyi içeren öğesini başlatır. <xref:Microsoft.VisualStudio.Package.CodeWindowManager>Daha sonra nesnesine yeni bir nesne verilir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> . <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>Yöntemi bir nesnesi alır <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> . Sınıfınızın bir örneğini döndürürler, <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> <xref:Microsoft.VisualStudio.Package.CodeWindowManager> <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> iç listeleri doldurmak için yönteminizi çağırır ve <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> nesneyi [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] açılan çubuk yöneticisine geçirir. Açılan çubuk Yöneticisi, sırasıyla, <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.SetDropdownBar%2A> <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> iki açılan çubuğu içeren nesneyi oluşturmak için nesneniz üzerindeki yöntemi çağırır <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar> .

 Giriş işareti değiştiğinde <xref:Microsoft.VisualStudio.Package.LanguageService.OnIdle%2A> Yöntemi yöntemini çağırır <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> . Taban <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> yöntemi, <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> gezinti çubuğunun durumunu güncelleştirmek için sınıfınıza yöntemi çağırır. <xref:Microsoft.VisualStudio.Package.DropDownMember>Bu yönteme bir nesne kümesi geçirirsiniz. Her nesne açılan kutudan bir girişi temsil eder.

## <a name="the-contents-of-the-navigation-bar"></a>Gezinti çubuğunun Içeriği
 Gezinti çubuğu genellikle türlerin bir listesini ve üye listesini içerir. Türlerin listesi, geçerli kaynak dosyada bulunan tüm türleri içerir. Tür adları, tüm ad alanı bilgilerini içerir. Aşağıda iki tür içeren C# kodu örneği verilmiştir:

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

 Tür listesi `TestLanguagePackage.TestLanguageService` ve görüntülenir `TestLanguagePackage.TestLanguageService.Tokens` .

 Üyeler listesi, türler listesinde seçilen türün kullanılabilir üyelerini görüntüler. Yukarıdaki kod örneğini kullanarak, `TestLanguagePackage.TestLanguageService` Seçilen türdür, Üyeler listesi özel üyeleri `tokens` ve içerir `serviceName` . İç yapı `Token` gösterilmez.

 Giriş işaretinin içine yerleştirildiğinde bir üyenin adını kalın hale getirmek için Üyeler listesini uygulayabilirsiniz. Üyeler ayrıca, giriş işaretinin Şu anda konumlandırılmış olduğu kapsam içinde olmadığını belirten gri renkte görüntülenebilir.

## <a name="enabling-support-for-the-navigation-bar"></a>Gezinti çubuğu desteğini etkinleştirme
 Gezinti çubuğu desteğini etkinleştirmek için `ShowDropdownBarOption` özniteliğinin parametresini olarak ayarlamanız gerekir <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> `true` . Bu parametre, <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A> özelliği ayarlar. Gezinti çubuğunu desteklemek için, <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> nesnesini <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> sınıfındaki yönteminde uygulamanız gerekir <xref:Microsoft.VisualStudio.Package.LanguageService> .

 <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>Yöntemi uygulamanızda, <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A> özelliği olarak ayarlandıysa `true` , bir <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> nesnesi döndürebilirsiniz. Nesneyi döndürmeyin gezinti çubuğu görüntülenmez.

 Gezinti çubuğunu gösterme seçeneği Kullanıcı tarafından ayarlanabilir, bu nedenle düzenleyici görünümü açıkken bu denetimin sıfırlanması mümkündür. Değişiklik gerçekleşmeden önce kullanıcının düzenleyici penceresini kapatması ve yeniden kapatması gerekir.

## <a name="implementing-support-for-the-navigation-bar"></a>Gezinti çubuğu için destek uygulama
 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>Yöntemi iki liste alır (her açılan liste için bir tane) ve her listedeki geçerli seçimi temsil eden iki değer. Listeler ve seçim değerleri güncelleştirilebilirler, bu durumda <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> yöntemin, `true` listelerin değiştiğini göstermek için döndürmesi gerekir.

 Türler açılan listesinde seçim değiştikçe, Üyeler listesinin yeni türü yansıtacak şekilde güncelleştirilmeleri gerekir. Üyeler listesinde gösterilen özellikler aşağıdakilerden biri olabilir:

- Geçerli türe ait üyelerin listesi.

- Kaynak dosyada bulunan tüm Üyeler, ancak mevcut türde olmayan tüm Üyeler gri renkte gösterilir. Kullanıcı yine de gri olan üyeleri seçebilir, bu nedenle hızlı gezinme için kullanılabilirler, ancak renk, seçili türün bir parçası olmadığını gösterir.

  <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>Yönteminin uygulanması genellikle aşağıdaki adımları gerçekleştirir:

1. Kaynak dosya için geçerli bildirimlerin bir listesini alın.

     Listeleri doldurmanız için çeşitli yollar vardır. Tek bir yaklaşım, <xref:Microsoft.VisualStudio.Package.LanguageService> <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> tüm bildirimlerin listesini döndüren özel bir ayrıştırma nedeni ile yöntemini çağıran sınıfının sürümünde özel bir yöntem oluşturmaktır. Başka bir yaklaşım, <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> yöntemi <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> özel ayrıştırma nedenine doğrudan yönteminden çağırmak olabilir. Üçüncü bir yaklaşım, <xref:Microsoft.VisualStudio.Package.AuthoringScope> sınıftaki son tam Ayrıştırma işleminin döndürdüğü sınıftaki bildirimleri önbelleğe almak <xref:Microsoft.VisualStudio.Package.LanguageService> ve bu yöntemi yönteminden elde etmek olabilir <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> .

2. Türlerin listesini doldurun veya güncelleştirin.

     Kaynak değiştiğinde ya da türlerin metin stilini geçerli giriş işareti konumuna göre değiştirmeyi seçtiyseniz türler listesinin içeriği güncelleştirilemeyebilir. Bu konumun yöntemine geçtiğini unutmayın <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> .

3. Geçerli giriş işareti konumuna göre türler listesinde seçilecek türü belirleyin.

     1. adımda elde edilen bildirimlerinde, geçerli giriş işareti konumunu kapsayan türü bulmak için arama yapabilir ve sonra bu türün Dizin türlerini türler listesine eklemek için türler listesinde arama yapabilirsiniz.

4. Seçilen türe göre üye listesini doldurun veya güncelleştirin.

     Üyeler listesi, **Üyeler** açılan listesinde o anda görüntülendiklerinizi yansıtır. Kaynak değiştirilirse veya yalnızca seçilen türün üyelerini görüntülüyorsanız ve seçilen tür değiştiyse, Üyeler listesinin içeriğinin güncellenmesi gerekebilir. Kaynak dosyadaki tüm üyeleri görüntülemeyi seçerseniz, şu anda seçili olan tür değiştiyse listedeki her üyenin metin stillendirme güncelleştirilmesi gerekir.

5. Geçerli giriş işareti konumuna göre üye listesinde seçilecek üyeyi belirleyin.

     Geçerli giriş işareti konumunu içeren üye için adım 1 ' de edinilen bildirimlerinde arama yapın, ardından üye listesinde bu üyenin üyelerini bulmak için üye listesini arayın.

6. `true`Listelerde veya her iki listedeki seçimlerde herhangi bir değişiklik yapılırsa döndürün.
