---
title: Seçenek Sayfaları Oluşturma | Microsoft Docs
description: Yönetilen paket çerçevesinden bir DialogPage sınıfı uygulayarak Visual Studio Araçlar menüsünün altında Seçenekler sayfası oluşturma hakkında bilgi alın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed package framework, creating Tools Options pages
- Tools Options pages [Visual Studio SDK], creating using managed package framework
ms.assetid: 1bf11fec-dece-4943-8053-6de1483c43eb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: d2724a8ce237f238c75e5f63f1621a5ae548f36d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122124691"
---
# <a name="create-options-pages"></a>Seçenek sayfaları oluşturma
Yönetilen paket [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] çerçevesinde, Araçlar menüsünün altına <xref:Microsoft.VisualStudio.Shell.DialogPage> Seçenekler sayfaları ekleyerek [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE'nin genişletmesinden türetilen **sınıflar.** 

 Belirli bir Araçlar Seçeneği sayfasını **uygulayan** bir nesne, nesnesi tarafından belirli VSPackage'larla <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> ilişkilendirildi.

 Ortam, IDE tarafından belirli bir  sayfa görüntülendiğinde belirli bir Araçlar Seçenekleri sayfasını uygulayan nesnenin örneğini oluşturur:

- Araçlar **Seçeneği** sayfası, VSPackage uygulayan nesne üzerinde değil, kendi nesnesine uygulanarak gerçekleştirilsin.

- Bir nesne birden çok Araç **Seçenekleri sayfası uygulayamaz.**

## <a name="register-as-a-tools-options-page-provider"></a>Araç Seçenekleri sayfa sağlayıcısı olarak kaydetme
 Araç Seçenekleri sayfaları aracılığıyla kullanıcı  yapılandırmasını destekleyen bir  VSPackage, uygulamaya uygulanan örneklerini uygulayarak bu Araç Seçenekleri <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> sayfalarını sağlayan nesneleri <xref:Microsoft.VisualStudio.Shell.Package> gösterir.

 Bir Araç Seçenekleri sayfası <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> uygulayan <xref:Microsoft.VisualStudio.Shell.DialogPage> türetilmiş her tür için bir **örneği** olması gerekir.

 Her örneği Araçlar Seçenekleri sayfasını uygulayan türü, Araç Seçenekleri sayfasını tanımlamak için kullanılan kategoriyi ve alt kategoriyi içeren dizeleri ve türü bir Araç Seçenekleri sayfası olarak kaydetmek için kaynak <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> **bilgilerini** kullanır.  

## <a name="persist-tools-options-page-state"></a>Kalıcı Araçlar Seçenekleri sayfa durumu
 Bir Araç **Seçenekleri sayfa** uygulaması otomasyon desteğinin etkinleştirildiğinde kaydedilirse, IDE diğer tüm Araç Seçenekleri sayfalarıyla birlikte sayfanın durumunu da **devam eder.**

 VSPackage, kullanarak kendi kalıcılıklarını <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> yönetebilir. Yalnızca bir veya diğer kalıcılık yöntemi kullanılmalıdır.

## <a name="implement-dialogpage-class"></a>DialogPage sınıfını uygulama
 VSPackage'ın türetilmiş tür uygulamasını sağlayan <xref:Microsoft.VisualStudio.Shell.DialogPage> bir nesne, aşağıdaki devralınan özelliklerden faydalanabilir:

- Varsayılan kullanıcı arabirimi penceresi.

- Sınıfına uygulanırsa veya özelliği sınıfına uygulanan için olarak ayarlanmışsa varsayılan <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A> bir `true` <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> kalıcılık mekanizması kullanılabilir.

- Otomasyon desteği.

  kullanarak Bir Araç Seçenekleri sayfası uygulayan **bir nesne için** en düşük <xref:Microsoft.VisualStudio.Shell.DialogPage> gereksinim, genel özelliklerin ek olmasıdır.

  Sınıf Bir Araç Seçenekleri sayfa **sağlayıcısı olarak** düzgün bir şekilde  kaydedilmişse,  genel özellikleri Araçlar menüsünün Seçenekler bölümünde bir özellik kılavuzu şeklinde kullanılabilir.

  Tüm bu varsayılan özellikler geçersiz kılınabilir. Örneğin, daha gelişmiş bir kullanıcı arabirimi oluşturmak için yalnızca varsayılan uygulamasının geçersiz kılınma <xref:Microsoft.VisualStudio.Shell.DialogPage.Window%2A> gerekir.

## <a name="example"></a>Örnek
 Seçenekler sayfasının basit bir "Merhaba dünya" uygulaması aşağıdaki gibidir. Menü Komutu seçeneğinin seçili olduğu Visual Studio paket şablonu tarafından  oluşturulan varsayılan projeye aşağıdaki kodu eklemek seçenek sayfası işlevselliğini yeterli düzeyde gösterir.

### <a name="description"></a>Açıklama
 Aşağıdaki sınıf, en az "Merhaba dünya" seçenekler sayfasını tanımlar. Açıldığında, kullanıcı bir özellik kılavuzunda `HelloWorld` ortak özelliği ayar herhangi bir şekilde ayarlamaz.

### <a name="code"></a>Kod
:::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/cs/class1.cs" id="Snippet11":::
:::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/vb/class1.vb" id="Snippet11":::

### <a name="description"></a>Açıklama
 Paket sınıfına aşağıdaki özniteliğin uygulanması, paket yüklenirken seçenekler sayfasını kullanılabilir yapar. Sayılar kategori ve sayfa için rastgele kaynak kimlikleridir ve sonundaki Boole değeri sayfanın otomasyonu destekleyip desteklemey olmadığını belirtir.

### <a name="code"></a>Kod
:::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/cs/uiusersettingstoolsoptionspagespackage.cs" id="Snippet07":::
:::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/vb/uiusersettingstoolsoptionspagespackage.vb" id="Snippet07":::

### <a name="description"></a>Açıklama
 Aşağıdaki olay işleyicisi, seçenekler sayfasında ayarlanmış özelliğin değerine bağlı olarak bir sonuç görüntüler. Sonucu açıkça özel seçenek sayfa türüne dönüştürerek sayfa tarafından ortaya çıkan özelliklere <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> erişmek için yöntemini kullanır.

 Paket şablonu tarafından oluşturulan bir projede, araçlar menüsüne eklenen varsayılan komuta eklemek için işlevden `MenuItemCallback` bu işlevi **çağırabilirsiniz.**

### <a name="code"></a>Kod
:::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/cs/uiusersettingstoolsoptionspagespackage.cs" id="Snippet08":::
:::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/vb/uiusersettingstoolsoptionspagespackage.vb" id="Snippet08":::

## <a name="see-also"></a>Ayrıca bkz.
- [Kullanıcı ayarlarını ve seçeneklerini genişletme](../../extensibility/extending-user-settings-and-options.md)
- [Seçenek sayfaları için otomasyon desteği](../../extensibility/internals/automation-support-for-options-pages.md)
