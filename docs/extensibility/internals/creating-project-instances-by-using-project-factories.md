---
title: Project fabrikaları kullanarak Project örnekleri oluşturma | Microsoft Docs
description: Visual Studio tümleşik geliştirme ortamında (ıde) proje fabrikaları kullanarak proje sınıfı örnekleri oluşturmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project factories
- projects [Visual Studio SDK], project factories
ms.assetid: 94c90012-8669-459c-af8e-307ac242c8c4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 1fc9fa9d4f10c59d4e17f2314cdbed80da26c3b5e24b115fb755c1fce9645b24
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121448201"
---
# <a name="create-project-instances-by-using-project-factories"></a>Proje fabrikalarını kullanarak proje örnekleri oluşturma
içindeki Project türler proje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nesneleri örnekleri oluşturmak için bir *proje fabrikası* kullanır. Proje fabrikası, cocreatable COM nesneleri için standart sınıf fabrikasına benzer. Ancak, proje nesneleri cocreatable değildir; Bunlar yalnızca bir proje fabrikası kullanılarak oluşturulabilirler.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE, bir kullanıcı var olan bir projeyi yüklediğinde veya içinde yeni bir proje oluşturduğunda VSPackage uygulamanızda uygulanan proje fabrikasını çağırır [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Yeni proje nesnesi, IDE 'yi **Çözüm Gezgini** doldurmak için yeterli bilgi sağlar. Yeni proje nesnesi, IDE tarafından başlatılan ilgili tüm Kullanıcı Arabirimi eylemlerini desteklemek için gereken arabirimleri de sağlar.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>Arabirimini projenizdeki bir sınıfta uygulayabilirsiniz. Genellikle kendi modülünde bulunur.

 Bir sahip tarafından toplanmakta olan projelerin proje dosyasında bir sahip anahtarı kalıcı hale getirilmesi gerekir. Yöntemi, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> sahip anahtarı olan bir projede çağrıldığında, sahip olan proje sahip anahtarını bir proje fabrikası GUID 'ine dönüştürür ve sonra `CreateProject` gerçek oluşturma işlemi için bu proje fabrikasında yöntemi çağırır.

## <a name="create-an-owned-project"></a>Sahip olunan bir proje oluşturma
 Sahip, iki aşamada sahip olunan bir proje oluşturur:

1. <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.PreCreateForOwner%2A>Yöntemini çağırarak. Bu, sahip olan projeye, giriş denetimi temelinde toplanmış bir proje nesnesi oluşturma şansı sağlar `IUnknown` . Sahip olan proje, iç `IUnknown` ve toplanmış nesneyi sahip projeye geri geçirir. Bu, sahip olan projeye iç depolamayı sağlar `IUnknown` .

2. <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>Yöntemini çağırarak. Sahip olunan proje, `IVsProjectFactory::CreateProject` sahip olmayan projeler için durum olduğu gibi çağırmak yerine bu yöntem çağrıldığında tüm örneklemeyi yapar. Giriş `VSOWNEDPROJECTOBJECT` numaralandırması genellikle toplanmış olan projem. Sahip proje, proje nesnesinin zaten oluşturulup oluşturulmadığını (tanımlama bilgisi NULL değere eşit değil) veya oluşturulması gerektiğini (tanımlama bilgisi eşittir NULL) belirleyebilmek için bu değişkeni kullanabilir.

   Project türler, cocreatable COM nesnesinin clsıd 'sine benzer şekilde benzersiz bir proje guıd 'si tarafından tanımlanır. Genellikle, bir proje fabrikası tek bir proje türünün örneklerini oluşturmayı işler, ancak bir proje fabrikası birden fazla proje türü GUID 'SI tutamamak mümkündür.

   Project türler, belirli bir dosya adı uzantısıyla ilişkilendirilir. Bir kullanıcı var olan bir proje dosyasını açmaya çalıştığında veya bir şablonu kopyalayarak yeni bir proje oluşturmaya çalışırsa, IDE ilgili proje GUID 'sini belirlemede dosyadaki uzantıyı kullanır.

   IDE, yeni bir proje oluşturmak mı yoksa belirli bir türdeki mevcut bir projeyi açmak mı gerektiğini belirlediğinde, IDE, gerekli proje fabrikasını uygulayan VSPackage 'ı bulmak için **[HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Projects]** altındaki sistem kayıt defterindeki bilgileri kullanır. IDE bu VSPackage 'ı yükler. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>Yönteminde, VSPackage, yöntemini çağırarak, onun proje fabrikasını IDE ile kaydetmesi gerekir <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes.RegisterProjectType%2A> .

   Arabirimin birincil yöntemi, `IVsProjectFactory` <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> iki senaryoyu ele almalıdır: mevcut bir projeyi açma ve yeni bir proje oluşturma. Çoğu proje, proje durumlarını proje dosyasında depolar. Genellikle yeni projeler, yönteme geçirilen şablon dosyasının bir kopyası yapılarak `CreateProject` ve sonra kopyayı açarak oluşturulur. Mevcut projeler, doğrudan yöntemine geçirilen proje dosyası açılarak oluşturulur `CreateProject` . `CreateProject`Yöntemi, gerektiğinde kullanıcıya ek kullanıcı arabirimi özelliklerini görüntüleyebilir.

   Proje ayrıca dosya ve proje durumunu veritabanı veya Web sunucusu gibi dosya sistemi dışında bir depolama mekanizmasıyla depolayabilirler. Bu durumda, yöntemine geçirilen dosya adı parametresi `CreateProject` gerçekte bir dosya sistemi yolu değildir ancak proje verilerini tanımlamak için benzersiz bir dize (URL). `CreateProject`Uygulanan uygun oluşturma sırasının tetiklenmesi için geçirilen şablon dosyalarını kopyalamanız gerekmez.

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes>
- [Denetim listesi: yeni proje türleri oluşturma](../../extensibility/internals/checklist-creating-new-project-types.md)
