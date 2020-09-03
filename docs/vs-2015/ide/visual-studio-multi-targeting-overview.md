---
title: Çoklu hedefleme genel bakış | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- targeting .NET Framework version [Visual Studio]
- versions [Visual Studio], targeting .NET Framework version
- multi-targeting [Visual Studio]
- multitargeting [Visual Studio]
ms.assetid: b1702c33-0672-4ebc-b779-2b324d6ea880
caps.latest.revision: 39
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e9e8b53c5bd4d6045d7582c24be865ae216f1114
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851083"
---
# <a name="visual-studio-multi-targeting-overview"></a>Visual Studio Çoklu Sürüm Desteğine Genel Bakış
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu sürümünde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] uygulamanız için gerekli olan sürümünü belirtebilirsiniz. Bu nedenle, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] önceki bir sürümde başlattığınız bir projeyi geliştirmeye devam etmek için bu sürümünü kullanmak istiyorsanız Framework hedefini değiştirmeniz gerekmez. Ayrıca, Framework 'ün farklı sürümlerini hedefleyen projeler içeren bir çözüm de oluşturabilirsiniz. Çerçeve hedefleme Ayrıca uygulamanın yalnızca belirtilen Framework sürümünde kullanılabilen işlevselliği kullanmasını garantilemeye yardımcı olur.

> [!TIP]
> Farklı platformlar için de uygulama hedefleyebilirsiniz. Daha fazla bilgi için bkz. [Çoklu hedefleme](../msbuild/msbuild-multitargeting-overview.md)

## <a name="framework-targeting-features"></a>Framework hedefleme özellikleri
 Framework Hedefleme aşağıdaki özellikleri içerir:

- Daha önceki bir sürümünü hedefleyen bir projeyi açtığınızda [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] otomatik olarak yükseltebilir veya hedefi olduğu gibi bırakabilirsiniz.

- Bir proje oluşturduğunuzda, hedeflemek istediğiniz öğesinin sürümünü belirtebilirsiniz [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .

- [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]Var olan bir projenin hedeflediği sürümünü değiştirebilirsiniz.

- Aynı çözümde çeşitli projelerin her birinde farklı bir sürümünü hedefleyebilirsiniz [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .

- [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]Projenin hedeflediği sürümünü değiştirdiğinizde, [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] başvurularda ve yapılandırma dosyalarında gerekli değişiklikleri yapar.

  Daha önceki bir sürümünü hedefleyen bir proje üzerinde çalışırken [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , Visual Studio geliştirme ortamını dinamik olarak aşağıdaki gibi değiştirir:

- **Yeni proje** iletişim kutusu, yeni **öğe Ekle** Iletişim kutusu, **Yeni Başvuru Ekle** iletişim kutusu ve hedeflenen sürümde kullanılamayan seçimleri atlamak için **hizmet başvurusu Ekle** iletişim kutusu içindeki öğelere filtre uygular.

- **Araç kutusundaki** özel denetimleri filtreleyerek, hedeflenen sürümde mevcut olmayan olanları kaldırabilir ve birden fazla denetim kullanılabilir olduğunda yalnızca en güncel denetimleri gösterebilirsiniz.

- Hedeflenen sürümde kullanılamayan dil özelliklerini atlamak için IntelliSense 'e filtre uygular.

- **Özellikler** penceresindeki özellikleri, hedeflenen sürümde mevcut olmayan olanları atlamak için filtreler.

- Hedeflenen sürümde kullanılamayan seçenekleri atlamak için menü seçeneklerini filtreler.

- Derlemeler için, derleyici sürümünü ve hedeflenen sürüm için uygun olan derleyici seçeneklerini kullanır.

> [!NOTE]
> Framework hedefleme, uygulamanızın doğru şekilde çalışacağını garanti etmez. Hedeflenen sürüme karşı çalıştığından emin olmak için uygulamanızı test etmeniz gerekir. .NET Framework 2,0 ' den önceki çerçeve sürümlerini hedeflenemez.

## <a name="selecting-a-target-framework-version"></a>Hedef çerçeve sürümü seçme
 Bir proje oluşturduğunuzda, [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] **Yeni proje** iletişim kutusunda hedef sürümü seçin. Kullanılabilir proje şablonlarının listesi seçime göre filtrelenmiştir. Mevcut bir projede, [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Proje Özellikleri iletişim kutusunda hedef sürümü değiştirebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: .NET Framework bir sürümünü hedefleme](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

> [!NOTE]
> Visual Studio 'nun Express sürümlerinde, **Yeni proje** iletişim kutusunda hedef Framework 'ü ayarlayamazsınız.

## <a name="resolving-system-and-user-assembly-references"></a>Sistem ve Kullanıcı derleme başvurularını çözümleme
 .NET Framework sürümünü hedeflemek için, önce uygun derleme başvurularını yüklemeniz gerekir. 2,0, 3,0 ve 3,5 .NET Framework sürümleri için derleme başvuruları, [Microsoft Indirme merkezi 'nden Microsoft Visual Studio](https://www.microsoft.com/download/details.aspx?id=25150) Web sitesinden indirebileceğiniz .NET Framework 3,5 SP1 'e dahildir. .NET Framework 3,5 Istemci profili için derleme başvuruları, .NET Framework 4, .NET Framework 4 Istemci profili ve Silverlight, [Visual Studio İndirmeleri](https://msdn.microsoft.com/vstudio/bb984878.aspx) Web sitesinden de kullanılabilir.

> [!NOTE]
> .NET Framework istemci profili, sınırlı bir kitaplık ve özellik kümesi sağlayan .NET Framework bir alt kümesidir. İstemci profilleri hakkında daha fazla bilgi için bkz. [.NET Framework Client Profile](https://msdn.microsoft.com/library/f0219919-1f02-4588-8704-327a62fd91f1).

 **Başvuru Ekle** iletişim kutusu, hedef sürüme ait olmayan sistem derlemelerini devre dışı bırakarak [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] bir projeye yanlışlıkla eklenememelidir. (Sistem derlemeleri bir sürümünde yer alan. dll dosyalarıdır [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .) Hedeflenen sürümden daha sonraki bir çerçeve sürümüne ait olan başvurular çözümlenmeyecektir ve bu tür bir başvuruya bağlı olan denetimler eklenemez. Bu tür bir başvuruyu etkinleştirmek istiyorsanız, [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] projenin hedefini başvuruyu içeren bir öğesine sıfırlayın.  Daha fazla bilgi için bkz. [Proje tasarımcısına giriş](https://msdn.microsoft.com/898dd854-c98d-430c-ba1b-a913ce3c73d7).

 Derleme başvuruları hakkında daha fazla bilgi için bkz. [tasarım zamanında derlemeleri çözme](../msbuild/resolving-assemblies-at-design-time.md).

## <a name="enabling-linq"></a>LINQ etkinleştiriliyor
 .NET Framework 3,5 veya sonraki bir sürümü hedeflediğinizde, System. Core 'a yönelik bir başvuru ve System. LINQ için proje düzeyi içeri aktarma (yalnızca Visual Basic) otomatik olarak eklenir. LINQ özelliklerini kullanmak istiyorsanız, seçenek çıkarımı ' nı da (yalnızca Visual Basic) açmanız gerekir. Hedefi önceki bir .NET Framework sürümü olarak değiştirirseniz başvuru ve içeri aktarma otomatik olarak kaldırılır. Daha fazla bilgi için bkz. [nasıl yapılır: LINQ projesi oluşturma](https://msdn.microsoft.com/library/a929e653-09a3-44be-881f-68ca33f192b2).

## <a name="see-also"></a>Ayrıca Bkz.
[Çoklu hedefleme](../msbuild/msbuild-multitargeting-overview.md) 
 [ASP.NET Web projeleri](https://msdn.microsoft.com/library/8b8145a9-62f6-4fc4-8a83-47b0487cbe76) 
 için Çoklu hedefleme .NET Framework [Platform uyumluluğu ve sistem gereksinimleri](/visualstudio/productinfo/vs2015-compatibility-vs)
