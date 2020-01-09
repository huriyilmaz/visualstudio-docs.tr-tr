---
title: MSBuild Multihedefleme 'ye Genel Bakış | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: eecbcd65-9fbc-4307-a321-46d3c3b79b12
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d54209624a7413bb5d968f212e669a4be8171b43
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595923"
---
# <a name="msbuild-multitargeting-overview"></a>MSBuild multihedefleme genel bakış
MSBuild 'i kullanarak, .NET Framework çeşitli sürümlerinden herhangi birini ve çeşitli sistem platformlarından herhangi birini çalıştırmak için bir uygulamayı derleyebilirsiniz. Örneğin, bir uygulamayı 32 bit platformda .NET Framework 2,0 ' de çalışacak şekilde derleyebilir ve aynı uygulamayı bir 64-bit platformunda .NET Framework 4,5 üzerinde çalışacak şekilde derleyebilirsiniz.

> [!IMPORTANT]
> "Çoklu hedefleme" adına rağmen bir proje aynı anda yalnızca bir çerçeveyi ve yalnızca bir platformu hedefleyebilir.

 MSBuild 'in hedeflediği bazı özellikler şunlardır:

- .NET Framework önceki bir sürümünü hedefleyen bir uygulama geliştirebilirsiniz, örneğin, 2,0, 3,5 veya 4 sürümleri.

- Örneğin, Silverlight çerçevesi gibi .NET Framework dışında bir çerçeveyi hedefleyebilirsiniz.

- Hedef çerçevenin önceden tanımlanmış bir alt kümesi olan bir *çerçeve profilini*hedefleyebilirsiniz.

- .NET Framework geçerli sürümü için bir hizmet paketi yayımlanmışsa, hedefleyebilirsiniz.

- MSBuild hedefleme, bir uygulamanın yalnızca hedeflenen çerçevede ve platformda kullanılabilir olan işlevleri kullanmasını güvence altına alır.

## <a name="target-framework-and-platform"></a>Hedef çerçeve ve platform
 *Hedef çerçeve* , bir projenin üzerinde çalışmak üzere oluşturulduğu .NET Framework sürümüdür ve *hedef platform* , projenin üzerinde çalışmak üzere oluşturulduğu sistem platformudur.  Örneğin, bir .NET Framework 2,0 uygulamasını, 802x86 işlemci ailesi (x86) ile uyumlu bir 32 bit platformda çalışacak şekilde hedeflemek isteyebilirsiniz. Hedef Framework ve hedef platformun birleşimi *hedef bağlam*olarak bilinir. Daha fazla bilgi için bkz. [hedef Framework ve hedef platform](../msbuild/msbuild-target-framework-and-target-platform.md).

## <a name="toolset-toolsversion"></a>Araç Takımı (ToolsVersion)
 Araç takımı, uygulamayı oluşturmak için kullanılan araçları, görevleri ve hedefleri birlikte toplar. Araç takımı, *CSC. exe* ve *Vbc. exe*gibi derleyiciler, ortak hedefler dosyası (*Microsoft. Common. targets*) ve ortak görev dosyası (*Microsoft. Common. Tasks*) gibi derleyicileri içerir. 4,5 araç takımı, 2,0, 3,0, 3,5, 4 ve 4,5 .NET Framework sürümlerini hedeflemek için kullanılabilir. Ancak, 2,0 araç takımı yalnızca 2,0 sürümünü .NET Framework hedeflemek için kullanılabilir. Daha fazla bilgi için bkz. [araç takımı (araçları sürümü)](../msbuild/msbuild-toolset-toolsversion.md).

## <a name="reference-assemblies"></a>Başvuru derlemeleri
 Araç takımı 'nda belirtilen başvuru derlemeleri bir uygulama tasarlamanıza ve oluşturmanıza yardımcı olur. Bu başvuru derlemeleri yalnızca belirli bir hedef derlemeyi etkinleştirmeyin, ancak Visual Studio IDE 'deki bileşenleri ve özellikleri hedefle uyumlu olanlarla kısıtlar. Daha fazla bilgi için bkz. [tasarım zamanında derlemeleri çözümleme](../msbuild/resolving-assemblies-at-design-time.md).

## <a name="configure-targets-and-tasks"></a>Hedefleri ve görevleri yapılandırma
 MSBuild hedeflerini ve görevleri, üzerinde çalıştığınız sunucudan önemli ölçüde farklı olan bağlamların hedeflemesini sağlamak için MSBuild ile işlem dışı çalışacak şekilde yapılandırabilirsiniz.  Örneğin, geliştirme bilgisayarı .NET Framework 4,5 ile 64 bit platformda çalışırken 32 bitlik bir .NET Framework 2,0 uygulamasını hedefleyebilirsiniz. Daha fazla bilgi için bkz. [hedefleri ve görevleri yapılandırma](../msbuild/configuring-targets-and-tasks.md).

## <a name="troubleshooting"></a>Sorun giderme
 Hedef bağlamın parçası olmayan bir derlemeye başvuru yapmayı denerseniz hatalarla karşılaşabilirsiniz. Bu hatalar ve bunlarla ilgili daha fazla bilgi için bkz. [.NET Framework Hedefleme hatalarını giderme](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).
