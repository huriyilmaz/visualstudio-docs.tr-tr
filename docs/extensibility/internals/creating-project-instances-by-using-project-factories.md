---
title: Project Fabrikaları Kullanarak Project Örnekleri | Microsoft Docs
description: Tümleşik geliştirme ortamında (IDE) proje fabrikalarını Visual Studio sınıf örnekleri oluşturma hakkında bilgi.
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
ms.openlocfilehash: 9c733308203cae49a79f722db4b6b1eec37f6a7e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122086683"
---
# <a name="create-project-instances-by-using-project-factories"></a>Proje fabrikalarını kullanarak proje örnekleri oluşturma
Project nesne örneklerini [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] oluşturmak *için bir* proje fabrikası kullanan bir proje türü. Proje fabrikası, ortak kullanılabilir COM nesneleri için standart bir sınıf fabrikasına benzer. Ancak, proje nesneleri birlikte kullanılabilir değildir; yalnızca bir proje fabrikası kullanılarak oluşturulabilirler.

 Kullanıcı mevcut bir projeyi yüklerken veya içinde yeni bir proje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] oluşturduğunda, IDE VSPackage'nıza uygulanan proje fabrikasını çağırır. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Yeni proje nesnesi, IDE'ye verilerle doldurmak için yeterli **Çözüm Gezgini.** Yeni proje nesnesi, IDE tarafından başlatılan tüm ilgili kullanıcı arabirimi eylemlerini desteklemek için gerekli arabirimleri de sağlar.

 Arabirimi <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> projenizin bir sınıfında uygulayabilirsiniz. Genellikle kendi modülünde bulunur.

 Sahip tarafından toplanmış olan projelerin proje dosyasında bir sahip anahtarı kalıcı olması gerekir. Yöntem, sahip anahtarı olan bir projede çağrıldı mı, sahip olunan proje sahip anahtarını proje fabrikası GUID'lerine dönüştürür ve ardından gerçek oluşturma işlemi için bu proje <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> `CreateProject` fabrikasında yöntemini arar.

## <a name="create-an-owned-project"></a>Sahip olunan proje oluşturma
 Sahip iki aşamada sahip olunan bir proje oluşturur:

1. yöntemini <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.PreCreateForOwner%2A> çağırarak. Bu, sahip olunan projeye giriş denetimine göre toplu bir proje nesnesi oluşturma şansı `IUnknown` verir. Sahip olunan proje, iç `IUnknown` ve toplanan nesneyi sahip projesine geri iletir. Bu, sahip olunan projeye iç depolanma şansı `IUnknown` verir.

2. yöntemini <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A> çağırarak. Sahip olunan proje, sahip olunan projeler için olduğu gibi bu yöntem çağrılsa bile tüm `IVsProjectFactory::CreateProject` örneklemelerini yapar. Giriş `VSOWNEDPROJECTOBJECT` numaralama genellikle toplu sahip olunan projedir. Sahip olunan proje, proje nesnesinin önceden oluşturulmuş olup olmadığını (tanımlama bilgisi NULL değerine eşit değildir) veya oluşturulacak (tanımlama bilgisi NULL değerine eşittir) belirlemek için bu değişkeni kullanabilir.

   Project türler, ortakolu bir COM nesnesinin CLSID'sinde olduğu gibi benzersiz bir proje GUID'si ile tanımlanır. Genellikle, bir proje fabrikası tek bir proje türünün örneklerini oluşturmayı ele almaktadır, ancak bir proje fabrikasının birden fazla proje türü GUID'sini işlemesi mümkündür.

   Project türleri belirli bir dosya adı uzantısıyla ilişkilendirildi. Kullanıcı mevcut bir proje dosyasını açmayı veya şablonu klonlama ile yeni bir proje oluşturma girişiminde bulunsa, IDE ilgili proje GUID'sini belirlemek için dosyanın uzantısını kullanır.

   IDE yeni bir proje oluşturması veya belirli bir türde mevcut projeyi açması gerekip gerek olmadığını belirler belirlemez, IDE gerekli proje fabrikasını hangi VSPackage'ın uygulaydığını bulmak için **[HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Projects]** altındaki sistem kayıt defterindeki bilgileri kullanır. IDE bu VSPackage'i yükler. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>yönteminde, VSPackage yöntemini çağırarak proje fabrikasını IDE'ye <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes.RegisterProjectType%2A> kaydetmesi gerekir.

   Arabirimin birincil `IVsProjectFactory` yöntemi, iki <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> senaryoyu işlemesi gereken yöntemidir: mevcut projeyi açma ve yeni proje oluşturma. Çoğu proje, proje durumunu bir proje dosyasında depolar. Genellikle yeni projeler, yönteme geçirilen şablon dosyasının bir kopyası oluşturularak `CreateProject` ve ardından kopya açarak oluşturulur. Mevcut projeler, doğrudan yöntemine geçirilen proje dosyası açarak `CreateProject` örneklenmiş olur. yöntemi, `CreateProject` gerektiğinde kullanıcıya ek kullanıcı arabirimi özellikleri gösterebilirsiniz.

   Proje ayrıca hiçbir dosya kullanmaz ve bunun yerine proje durumunu veritabanı veya Web sunucusu gibi dosya sistemi dışında bir depolama mekanizmasında depolar. Bu durumda, yöntemine geçirilen dosya adı parametresi aslında proje verilerini tanımlamak için bir dosya sistemi yolu değil benzersiz bir `CreateProject` dizedir (URL). Yürütülecek uygun oluşturma sırasını tetiklemek için geçirilen `CreateProject` şablon dosyalarını kopyalamanız gerekli değildir.

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes>
- [Denetim listesi: Yeni proje türleri oluşturma](../../extensibility/internals/checklist-creating-new-project-types.md)
