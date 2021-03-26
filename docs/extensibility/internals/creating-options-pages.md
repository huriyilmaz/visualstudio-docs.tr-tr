---
title: Seçenek sayfaları oluşturuluyor | Microsoft Docs
description: Yönetilen paket çerçevesinden bir DialogPage sınıfı uygulayarak Visual Studio 'daki Araçlar menüsü altında Seçenekler sayfası oluşturmayı öğrenin.
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
ms.workload:
- vssdk
ms.openlocfilehash: 2e7513617ab4ee4a051dd48cd110ecb2c5e22495
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105056847"
---
# <a name="create-options-pages"></a>Seçenek sayfaları oluşturma
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Yönetilen paket çerçevesinde, <xref:Microsoft.VisualStudio.Shell.DialogPage> [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **Araçlar** menüsünün altına **Seçenekler** sayfası ekleyerek IDE 'yi genişletten türetilmiş sınıflar.

 Belirli bir **Araçlar seçeneği** sayfasını uygulayan nesne, nesne tarafından belirli VSPackages ile ilişkilendirilir <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> .

 Ortam, belirli bir sayfa IDE tarafından görüntülenirken belirli bir **araç seçenekleri** sayfasını uygulayan nesneyi örneklendiren için:

- Bir **araç seçeneği** sayfası, VSPackage uygulayan nesne üzerinde değil, kendi nesnesine uygulanmalıdır.

- Bir nesne birden çok **araç seçenekleri** sayfası uygulayamaz.

## <a name="register-as-a-tools-options-page-provider"></a>Araç seçenekleri sayfa sağlayıcısı olarak kaydet
 **Araç seçenekleri** sayfaları aracılığıyla Kullanıcı yapılandırmasını destekleyen VSPackage, uygulamaya uygulanan örnekleri uygulayarak bu **araç seçenekleri** sayfalarını sağlayan nesneleri gösterir <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> <xref:Microsoft.VisualStudio.Shell.Package> .

 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> <xref:Microsoft.VisualStudio.Shell.DialogPage> Bir **araç seçenekleri** sayfası uygulayan her türetilmiş tür için bir örnek olmalıdır.

 Her bir örneği, Araçlar Seçenekler sayfasını <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> uygulayan türü  , bir **araç seçenekleri** sayfasını tanımlamak için kullanılan kategori ve alt kategoriyi Içeren dizeleri ve türü bir **araç seçenekleri** sayfası olarak kaydetmek için kaynak bilgilerini kullanır.

## <a name="persist-tools-options-page-state"></a>Kalıcı Araçlar Seçenekler sayfası durumu
 Bir **araç seçenekleri** sayfası uygulamasının Otomasyon desteği etkinken kayıtlı olması halınde, IDE sayfanın durumunu diğer tüm **araç seçenekleri** sayfalarıyla birlikte sürdürür.

 Bir VSPackage, kullanarak kendi kalıcılığını yönetebilir <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> . Yalnızca bir veya başka bir kalıcılık yöntemi kullanılmalıdır.

## <a name="implement-dialogpage-class"></a>DialogPage sınıfını Uygula
 Bir VSPackage 'ın türetilmiş bir tür uygulamasını sağlayan bir nesne <xref:Microsoft.VisualStudio.Shell.DialogPage> , aşağıdaki devralınmış özelliklerden faydalanabilir:

- Varsayılan bir kullanıcı arabirimi penceresi.

- <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>Sınıfına uygulandığında veya <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A> özelliği `true` sınıfına uygulanan için olarak ayarlandıysa, varsayılan bir Kalıcılık mekanizması kullanılabilir <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> .

- Otomasyon desteği.

  Kullanarak bir **araç seçenekleri** sayfası uygulayan bir nesne için en düşük gereksinim, <xref:Microsoft.VisualStudio.Shell.DialogPage> ortak özelliklerin eklenmalarıdır.

  Sınıf bir **araç seçenekleri** sayfa sağlayıcısı olarak düzgün kaydedilmişse, bir özellik Kılavuzu formundaki **Araçlar** menüsünün **Seçenekler** bölümünde ortak özellikleri kullanılabilir.

  Tüm bu varsayılan özellikler geçersiz kılınabilir. Örneğin, daha karmaşık bir kullanıcı arabirimi oluşturmak için yalnızca varsayılan uygulamasının geçersiz kılınması gerekir <xref:Microsoft.VisualStudio.Shell.DialogPage.Window%2A> .

## <a name="example"></a>Örnek
 Aşağıda, bir Seçenekler sayfasının basit bir "Hello World" uygulamasıdır. Aşağıdaki kodu **menü komutu** seçeneği seçili olan Visual Studio paket şablonu tarafından oluşturulan varsayılan bir projeye eklemek, seçenek sayfası işlevselliğini yeterince gösterir.

### <a name="description"></a>Description
 Aşağıdaki sınıf, en düşük bir "Hello World" seçenekleri sayfasını tanımlar. Açıldığında, Kullanıcı `HelloWorld` bir özellik kılavuzunda ortak özelliği ayarlayabilir.

### <a name="code"></a>Kod
 [!code-csharp[UI_UserSettings_ToolsOptionPages#11](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_1.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#11](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_1.vb)]

### <a name="description"></a>Description
 Aşağıdaki öznitelik paket sınıfına uygulandığında, paket yüklendiğinde Seçenekler sayfası kullanılabilir hale gelir. Sayılar, kategori ve sayfa için rastgele kaynak kimliklerdir ve sonundaki Boole değeri sayfanın Otomasyonu destekleyip desteklemediğini belirtir.

### <a name="code"></a>Kod
 [!code-csharp[UI_UserSettings_ToolsOptionPages#07](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_2.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#07](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_2.vb)]

### <a name="description"></a>Description
 Aşağıdaki olay işleyicisi, Seçenekler sayfasında ayarlanmış özelliğin değerine bağlı olarak bir sonuç görüntüler. Bu yöntem, bir <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> yöntemi, sayfanın açığa çıkarılan özelliklerine erişmek için özel seçenek sayfası türüne açıkça bir atama ile kullanır.

 Paket şablonu tarafından oluşturulan bir proje söz konusu olduğunda, `MenuItemCallback` **araç** menüsüne eklenen varsayılan komuta eklemek için bu işlevi işlevinden çağırın.

### <a name="code"></a>Kod
 [!code-csharp[UI_UserSettings_ToolsOptionPages#08](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_3.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#08](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_3.vb)]

## <a name="see-also"></a>Ayrıca bkz.
- [Kullanıcı ayarlarını ve seçeneklerini genişletme](../../extensibility/extending-user-settings-and-options.md)
- [Seçenekler sayfaları için Otomasyon desteği](../../extensibility/internals/automation-support-for-options-pages.md)
