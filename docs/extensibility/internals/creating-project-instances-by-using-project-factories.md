---
title: Proje Fabrikalarını Kullanarak Proje Örnekleri Oluşturma | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project factories
- projects [Visual Studio SDK], project factories
ms.assetid: 94c90012-8669-459c-af8e-307ac242c8c4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 31ba5dd11af18f8a723b2271544eff2bd292e2e8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709056"
---
# <a name="create-project-instances-by-using-project-factories"></a>Proje fabrikalarını kullanarak proje örnekleri oluşturma
Proje nesneleri [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] örnekleri oluşturmak için bir *proje fabrikası* kullanır. Proje fabrikası, cocreatable COM nesneleri için standart sınıf fabrika benzer. Ancak, proje nesneleri cocreatable değildir; yalnızca bir proje fabrikası kullanılarak oluşturulabilir.

 IDE, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bir kullanıcı varolan bir projeyi yüklerken veya 'de yeni bir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]proje oluşturduğunda, VSPackage'ınızda uygulanan proje fabrikasını çağırır. Yeni proje nesnesi, IDE'ye **Çözüm Gezgini'ni**doldurmak için yeterli bilgi sağlar. Yeni proje nesnesi, IDE tarafından başlatılan tüm ilgili Kullanıcı Arabirimi eylemlerini desteklemek için gerekli arabirimleri de sağlar.

 Projenizde <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> arabirimi bir sınıfta uygulayabilirsiniz. Genellikle, kendi modülünde bulunur.

 Bir sahibi tarafından biraraya desteklenmesini destekleyen projelerin proje dosyasında bir sahip anahtarını devam etmesi gerekir. Yöntem, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> sahibi anahtarı olan bir projede çağrıldığında, sahip olduğu proje sahibi anahtarını `CreateProject` bir proje fabrikası GUID'e dönüştürür ve gerçek oluşturmayı yapmak için bu proje fabrikasındaki yöntemi çağırır.

## <a name="create-an-owned-project"></a>Sahip olunan bir proje oluşturma
 Sahibi, sahip olunan bir projeyi iki aşamada oluşturur:

1. <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.PreCreateForOwner%2A> Yöntemi arayarak. Bu, sahip olunan projeye giriş denetlemeyi temel alan toplu `IUnknown`bir proje nesnesi oluşturma şansı verir. Sahip olunan proje, iç `IUnknown` ve toplu nesneyi sahibi projeye geri geçirir. Bu, sahip olunan projeye iç `IUnknown`alanı depolama şansı verir.

2. <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A> Yöntemi arayarak. Sahip olunan proje, sahip olunmayan projelerde `IVsProjectFactory::CreateProject` olduğu gibi çağrılmak yerine bu yöntem çağrıldığında tüm anlık durumunu yapar. Giriş `VSOWNEDPROJECTOBJECT` numaralandırma genellikle toplanan ait projedir. Sahip olunan proje, proje nesnesinin zaten oluşturulup oluşturulmadığını (çerez null'a eşit değildir) veya oluşturulması gerekeni (çerez eşittir NULL) belirlemek için bu değişkeni kullanabilir.

   Proje türleri, cocreatable COM nesnesinin CLSID'sine benzer benzersiz bir proje GUID tarafından tanımlanır. Genellikle, bir proje fabrikası tek bir proje türüörnekleri oluşturmayı işler, ancak bir proje fabrikasının birden fazla proje türü GUID'i işlemesi mümkündür.

   Proje türleri belirli bir dosya adı uzantısı ile ilişkilidir. Bir kullanıcı varolan bir proje dosyasını açmaya çalıştığında veya şablonklonlayarak yeni bir proje oluşturmaya çalıştığında, IDE ilgili proje GUID'ini belirlemek için dosyaüzerindeki uzantıyı kullanır.

   IDE, yeni bir proje oluşturması mı yoksa belirli bir türdeki varolan bir projeyi açması mı gerektiğini belirler belirlemez, IDE sistem kayıt defterindeki bilgileri **[HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Projects]** altında kullanır ve hangi VSPackage'in gerekli proje fabrikasını uyguladığını bulur. IDE bu VSPackage yükler. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> Yöntemde, VSPackage yöntemi çağırarak proje fabrikasını IDE'ye kaydettirmelidir. <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes.RegisterProjectType%2A>

   `IVsProjectFactory` Arabirimin birincil <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>yöntemi, iki senaryoyu işlemek tir: varolan bir projeyi açmak ve yeni bir proje oluşturmak. Çoğu proje, proje durumunu bir proje dosyasında depolar. Genellikle, şablon dosyasının bir kopyasını `CreateProject` yönteme geçirerek ve ardından kopyayı açarak yeni projeler oluşturulur. Mevcut projeler, yönteme `CreateProject` geçirilen proje dosyası nın doğrudan açılarak anında doldurulmaktadır. Yöntem `CreateProject` gerektiğinde kullanıcıya ek Kullanıcı-ı OI özellikleri görüntüleyebilir.

   Proje ayrıca hiçbir dosya kullanamaz ve bunun yerine, proje durumunu veritabanı veya Web sunucusu gibi dosya sistemi dışında bir depolama mekanizmasında depolayabilir. Bu durumda, `CreateProject` yönteme geçirilen dosya adı parametresi aslında bir dosya sistemi yolu değil, proje verilerini tanımlamak için benzersiz bir dize-bir URL'dir. Yürütülecek uygun yapı sırasını tetiklemek `CreateProject` için geçirilen şablon dosyalarını kopyalamanız gerekmez.

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes>
- [Denetim Listesi: Yeni proje türleri oluşturma](../../extensibility/internals/checklist-creating-new-project-types.md)
