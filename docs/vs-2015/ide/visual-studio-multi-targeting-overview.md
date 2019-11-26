---
title: Multi-Targeting'e genel bakış | Microsoft Docs
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
ms.openlocfilehash: 6a816981b41dd8ca2a2119bbd99c776c6a7e2436
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74296880"
---
# <a name="visual-studio-multi-targeting-overview"></a>Visual Studio Çoklu Sürüm Desteğine Genel Bakış
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]sürümünde, uygulamanız için gerekli [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] sürümünü belirtebilirsiniz. Bu nedenle, önceki bir sürümde başlattığınız bir projeyi geliştirmeye devam etmek için [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 'un bu sürümünü kullanmak istiyorsanız, Framework hedefini değiştirmeniz gerekmez. Ayrıca, farklı sürümlerini hedefleyen framework'ün projeleri içeren bir çözüm oluşturabilirsiniz. Çerçeve hedefleme ayrıca uygulamanın yalnızca belirtilen çerçeve sürümünde kullanılabilir olan işlevleri kullanmasının garantilenmesine yardımcı olur.

> [!TIP]
> Ayrıca, farklı platformlar için uygulamaları hedefleyebilirsiniz. Daha fazla bilgi için bkz. [Çoklu hedefleme](../msbuild/msbuild-multitargeting-overview.md)

## <a name="framework-targeting-features"></a>Çerçeve hedefleme özellikleri
 Çerçeve hedefleme şu özellikleri içerir:

- [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]önceki bir sürümünü hedefleyen bir projeyi açtığınızda, [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] otomatik olarak yükseltebilir veya hedefi olduğu gibi bırakabilir.

- Bir proje oluşturduğunuzda, hedeflemek istediğiniz [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] sürümünü belirtebilirsiniz.

- Var olan bir projenin hedeflediği [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] sürümünü değiştirebilirsiniz.

- Aynı çözümdeki birçok projenin [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] farklı bir sürümünü hedefleyebilirsiniz.

- Bir projenin hedeflediği [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] sürümünü değiştirdiğinizde [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], başvurularda ve yapılandırma dosyalarında gerekli değişiklikleri yapar.

  [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]önceki bir sürümünü hedefleyen bir projede çalışırken, Visual Studio geliştirme ortamını dinamik olarak aşağıdaki gibi değiştirir:

- **Yeni proje** iletişim kutusu, yeni **öğe Ekle** Iletişim kutusu, **Yeni Başvuru Ekle** iletişim kutusu ve hedeflenen sürümde kullanılamayan seçimleri atlamak için **hizmet başvurusu Ekle** iletişim kutusu içindeki öğelere filtre uygular.

- **Araç kutusundaki** özel denetimleri filtreleyerek, hedeflenen sürümde mevcut olmayan olanları kaldırabilir ve birden fazla denetim kullanılabilir olduğunda yalnızca en güncel denetimleri gösterebilirsiniz.

- Bu, hedeflenen sürümde olmayan dil özelliklerini atlamak için Intellisense'e filtre uygular.

- **Özellikler** penceresindeki özellikleri, hedeflenen sürümde mevcut olmayan olanları atlamak için filtreler.

- Bu, hedeflenen sürümde kullanılabilir olmayan seçenekleri atlamak için menü seçeneklerine filtre uygular.

- Derlemeler için derleyici ve derleyici seçenekleri hedeflenen sürüm için uygun sürümünü kullanır.

> [!NOTE]
> Çerçeve hedefleme, uygulamanızın doğru şekilde çalışacağını garanti etmez. Hedeflenen sürümde çalışacağından çalıştığından emin olmak için uygulamanızı test etmeniz gerekir. .NET Framework 2. 0 ' daha eski framework sürümlerini hedefleyemezsiniz.

## <a name="selecting-a-target-framework-version"></a>Hedef Framework sürüm seçme
 Bir proje oluşturduğunuzda, **Yeni proje** iletişim kutusunda hedef [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] sürümünü seçin. Kullanılabilir proje şablonları listesinde, seçime göre filtrelenir. Mevcut bir projede, proje özellikleri iletişim kutusunda hedef [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] sürümünü değiştirebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: .NET Framework bir sürümünü hedefleme](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

> [!NOTE]
> Visual Studio 'nun Express sürümlerinde, **Yeni proje** iletişim kutusunda hedef Framework 'ü ayarlayamazsınız.

## <a name="resolving-system-and-user-assembly-references"></a>Sistem ve kullanıcı derleme başvurularını çözümleme
 Bir .NET Framework sürümünü hedeflemek için önce uygun derleme başvurularını yüklemeniz gerekir. 2,0, 3,0 ve 3,5 .NET Framework sürümleri için derleme başvuruları, [Microsoft Indirme merkezi 'nden Microsoft Visual Studio](https://www.microsoft.com/download/details.aspx?id=25150) Web sitesinden indirebileceğiniz .NET Framework 3,5 SP1 'e dahildir. .NET Framework 3,5 Istemci profili için derleme başvuruları, .NET Framework 4, .NET Framework 4 Istemci profili ve Silverlight, [Visual Studio İndirmeleri](https://go.microsoft.com/fwlink/?LinkId=179687) Web sitesinden de kullanılabilir.

> [!NOTE]
> .NET Framework istemci profili, kitaplıkların ve özelliklerin sınırlı bir kümesini sağlayan .NET Framework'ün bir alt kümesidir. İstemci profilleri hakkında daha fazla bilgi için bkz. [.NET Framework Client Profile](https://msdn.microsoft.com/library/f0219919-1f02-4588-8704-327a62fd91f1).

 **Başvuru Ekle** iletişim kutusu, bir projeye yanlışlıkla eklenememesi için hedef [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] sürümüyle ilgili olmayan sistem derlemelerini devre dışı bırakır. (Sistem derlemeleri [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] sürümünde yer alan. dll dosyalarıdır.) Hedeflenen sürümden daha sonraki bir çerçeve sürümüne ait olan başvurular çözümlenmeyecektir ve bu tür bir başvuruya bağlı olan denetimler eklenemez. Böyle bir başvuruyu etkinleştirmek istiyorsanız, projenin [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] hedefini başvuruyu içeren bir tane olarak sıfırlayın.  Daha fazla bilgi için bkz. [Proje tasarımcısına giriş](https://msdn.microsoft.com/898dd854-c98d-430c-ba1b-a913ce3c73d7).

 Derleme başvuruları hakkında daha fazla bilgi için bkz. [tasarım zamanında derlemeleri çözme](../msbuild/resolving-assemblies-at-design-time.md).

## <a name="enabling-linq"></a>LINQ'i etkinleştirme
 .NET Framework 3.5 veya sonraki sürümler, bir System.Core başvurusu ve bir proje düzeyi içeri aktarma (yalnızca Visual Basic'te) System.Linq hedeflediğinizde otomatik olarak eklenir. LINQ özelliklerini kullanmak istiyorsanız, ayrıca Option Infer (yalnızca Visual Basic'te) açmanız gerekir. Hedefi önceki bir .NET Framework sürümü ile değiştirirseniz başvuru ve içe aktarma otomatik olarak kaldırılır. Daha fazla bilgi için bkz. [nasıl yapılır: LINQ projesi oluşturma](https://msdn.microsoft.com/library/a929e653-09a3-44be-881f-68ca33f192b2).

## <a name="see-also"></a>Ayrıca Bkz.
Çoklu [hedefleme](../msbuild/msbuild-multitargeting-overview.md)
[, platform uyumluluğu ve sistem gereksinimleri](/visualstudio/productinfo/vs2015-compatibility-vs)
[ASP.NET Web projeleri için Çoklu hedefleme .NET Framework](https://msdn.microsoft.com/library/8b8145a9-62f6-4fc4-8a83-47b0487cbe76)
