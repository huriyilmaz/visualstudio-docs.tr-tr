---
title: Seçenekler Sayfaları Oluşturma | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed package framework, creating Tools Options pages
- Tools Options pages [Visual Studio SDK], creating using managed package framework
ms.assetid: 1bf11fec-dece-4943-8053-6de1483c43eb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 368efaa78a56723d4a72c482bea9ee739385127e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709145"
---
# <a name="create-options-pages"></a>Seçenekler sayfaları oluşturma
Yönetilen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] paket çerçevesinde, Araçlar <xref:Microsoft.VisualStudio.Shell.DialogPage> menüsünün [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] altına **Seçenekler** sayfaları ekleyerek **Tools** IDE'den türetilen sınıflar IDE'yi genişletir.

 Belirli bir Araçlar **Seçeneği** sayfasını uygulayan bir <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> nesne, nesne tarafından belirli VSPackages ile ilişkilidir.

 Çünkü ortam, belirli bir sayfa IDE tarafından görüntülendiğinde belirli bir **Araç Seçenekleri** sayfasını uygulayan nesneyi anında uygular:

- **Bir Araç Seçeneği** sayfası, VSPackage uygulayan nesneüzerinde değil, kendi nesnesi üzerinde uygulanmalıdır.

- Bir nesne birden çok **Araç Seçeneği** sayfası uygulayamaz.

## <a name="register-as-a-tools-options-page-provider"></a>Araç Seçenekleri sayfa sağlayıcısı olarak kaydolun
 **Araçlar Seçenekleri** sayfaları aracılığıyla kullanıcı yapılandırmasını destekleyen BIR VSPackage, <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> <xref:Microsoft.VisualStudio.Shell.Package> uygulamaya uygulanan örnekleri uygulayarak bu Araçlar **Seçenekleri** sayfalarını sağlayan nesneleri gösterir.

 **Araç Seçenekleri** sayfasını <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> uygulayan <xref:Microsoft.VisualStudio.Shell.DialogPage>her tür için bir örnek olmalıdır.

 **Her örneği, Araçlar Seçenekleri** sayfasını uygulayan türü, Bir Araç **Seçenekleri** sayfasını tanımlamak için kullanılan kategori ve alt kategoriyi içeren dizeleri ve türü **Araç Seçenekleri** sayfası olarak kaydetmek için kaynak bilgilerini <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> kullanır.

## <a name="persist-tools-options-page-state"></a>Kalıcı Araçlar Seçenekleri sayfa durumu
 Bir **Araç Seçenekleri** sayfası uygulaması otomasyon desteği etkinleştirilmiş olarak kaydedilmişse, IDE diğer tüm **Araç Seçenekleri** sayfalarıyla birlikte sayfanın durumunu devam eder.

 Bir VSPackage kullanarak <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>kendi kalıcılığını yönetebilirsiniz. Yalnızca bir veya diğer kalıcılık yöntemi kullanılmalıdır.

## <a name="implement-dialogpage-class"></a>DialogPage sınıfIni uygula
 VSPackage'ın türetilmiş bir türde uygulanmasını sağlayan bir <xref:Microsoft.VisualStudio.Shell.DialogPage>nesne aşağıdaki devralınan özelliklerden yararlanabilir:

- Varsayılan kullanıcı arabirimi penceresi.

- Sınıfa <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> uygulanırsa veya <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A> özellik sınıfa uygulanan için ayarlanmışsa `true` <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> varsayılan kalıcılık mekanizması kullanılabilir.

- Otomasyon desteği.

  **Araç Seçenekleri** sayfasını kullanan <xref:Microsoft.VisualStudio.Shell.DialogPage> bir nesne için en az gereksinim, ortak özelliklerin eklenmesidir.

  Sınıf **Araç Seçenekleri** sayfa sağlayıcısı olarak düzgün bir şekilde kaydedilmişse, ortak özellikleri **Araçlar** menüsünün **Seçenekler** bölümünde özellik ızgarası biçiminde kullanılabilir.

  Tüm bu varsayılan özellikler geçersiz kılınabilir. Örneğin, daha gelişmiş bir kullanıcı arabirimi oluşturmak için <xref:Microsoft.VisualStudio.Shell.DialogPage.Window%2A>yalnızca varsayılan uygulama geçersiz kılma gerektirir.

## <a name="example"></a>Örnek
 Aşağıda bir seçenek sayfasının basit bir "Merhaba dünya" uygulamasıdır. Seçilen **Menü Komutu** seçeneğiyle Visual Studio paket şablonu tarafından oluşturulan varsayılan bir projeye aşağıdaki kodun eklenmesi seçenek sayfası işlevselliğini yeterince gösterir.

### <a name="description"></a>Açıklama
 Aşağıdaki sınıf en az "Merhaba dünya" seçenekleri sayfasını tanımlar. Açıldığında, kullanıcı ortak `HelloWorld` özelliği bir özellik ızgarasında ayarlayabilir.

### <a name="code"></a>Kod
 [!code-csharp[UI_UserSettings_ToolsOptionPages#11](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_1.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#11](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_1.vb)]

### <a name="description"></a>Açıklama
 Paket sınıfına aşağıdaki özniteliği uygulamak, paket yüklendiğinde seçenekler sayfasını kullanılabilir hale getirir. Sayılar kategori ve sayfa için rasgele kaynak kimlikleridir ve sonundaki Boolean değeri sayfanın otomasyonu destekleyip desteklemediğini belirtir.

### <a name="code"></a>Kod
 [!code-csharp[UI_UserSettings_ToolsOptionPages#07](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_2.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#07](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_2.vb)]

### <a name="description"></a>Açıklama
 Aşağıdaki olay işleyicisi, seçenekler sayfasında ayarlanan özelliğin değerine bağlı olarak bir sonuç görüntüler. Bu, <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> sayfatarafından açığa çıkarılan özelliklere erişmek için özel seçenek sayfa türüne açıkça atılarak sonucu içeren yöntemi kullanır.

 Paket şablonu tarafından oluşturulan bir proje söz konusu `MenuItemCallback` olduğunda, **araçlar** menüsüne eklenen varsayılan komuta eklemek için bu işlevi işlevden çağırın.

### <a name="code"></a>Kod
 [!code-csharp[UI_UserSettings_ToolsOptionPages#08](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_3.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#08](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_3.vb)]

## <a name="see-also"></a>Ayrıca bkz.
- [Kullanıcı ayarlarını ve seçeneklerini genişletme](../../extensibility/extending-user-settings-and-options.md)
- [Seçenekler sayfaları için otomasyon desteği](../../extensibility/internals/automation-support-for-options-pages.md)
