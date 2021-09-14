---
title: MSBuild Çoklu hedeflemeye genel bakış | Microsoft Docs
description: MSBuild, .NET Framework çeşitli sürümlerinden herhangi birinde ve çeşitli sistem platformlarından herhangi birinde çalışacak şekilde bir uygulamayı derlemek için nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: eecbcd65-9fbc-4307-a321-46d3c3b79b12
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: a71c3c774e512d012b1f1bbd99a8e00aa1304cda
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627057"
---
# <a name="msbuild-multitargeting-overview"></a>MSBuild çoklu sürüm desteğine genel bakış

MSBuild kullanarak, bir uygulamayı .NET Framework çeşitli sürümlerinden herhangi birinde ve çeşitli sistem platformlarından herhangi birinde çalışacak şekilde derleyebilirsiniz. örneğin, bir uygulamayı 32 bit platformda .NET Framework 2,0 ' de çalışacak şekilde derleyebilir ve aynı uygulamayı bir 64-bit platformunda .NET Framework 4,5 üzerinde çalışacak şekilde derleyebilirsiniz.

> [!IMPORTANT]
> "Çoklu hedefleme" adına rağmen bir proje aynı anda yalnızca bir çerçeveyi ve yalnızca bir platformu hedefleyebilir.

 bunlar MSBuild hedeflediği özelliklerden bazılarıdır:

- .NET Framework önceki bir sürümünü hedefleyen bir uygulama geliştirebilirsiniz, örneğin, 2,0, 3,5 veya 4 sürümleri.

- örneğin, Silverlight çerçevesi gibi .NET Framework dışında bir çerçeveyi hedefleyebilirsiniz.

- Hedef çerçevenin önceden tanımlanmış bir alt kümesi olan bir *çerçeve profilini* hedefleyebilirsiniz.

- .NET Framework geçerli sürümü için bir hizmet paketi yayımlanmışsa, hedefleyebilirsiniz.

- MSBuild hedefleme, bir uygulamanın yalnızca hedeflenen çerçevede ve platformda kullanılabilir olan işlevleri kullanmasını güvence altına alır.

## <a name="target-framework-and-platform"></a>Hedef çerçeve ve platform

 *hedef çerçeve* , bir projenin üzerinde çalışmak üzere oluşturulduğu .NET Framework sürümüdür ve *hedef platform* , projenin üzerinde çalışmak üzere oluşturulduğu sistem platformudur.  örneğin, 80x86 işlemci ailesi (x86) ile uyumlu bir 32 bit platformda çalıştırmak üzere bir .NET Framework 2,0 uygulamasını hedeflemek isteyebilirsiniz. Hedef Framework ve hedef platformun birleşimi *hedef bağlam* olarak bilinir. Daha fazla bilgi için bkz. [hedef Framework ve hedef platform](../msbuild/msbuild-target-framework-and-target-platform.md).

## <a name="toolset-toolsversion"></a>Araç Takımı (ToolsVersion)

 Araç takımı, uygulamayı oluşturmak için kullanılan araçları, görevleri ve hedefleri birlikte toplar. Araç takımı, *csc.exe* ve *vbc.exe*, ortak hedefler dosyası (*Microsoft. Common. targets*) ve ortak görevler dosyası (*Microsoft. Common. Tasks*) gibi derleyiciler içerir. 4,5 araç takımı, 2,0, 3,0, 3,5, 4 ve 4,5 .NET Framework sürümlerini hedeflemek için kullanılabilir. ancak, 2,0 araç takımı yalnızca 2,0 sürümünü .NET Framework hedeflemek için kullanılabilir. Daha fazla bilgi için bkz. [araç takımı (araçları sürümü)](../msbuild/msbuild-toolset-toolsversion.md).

## <a name="reference-assemblies"></a>Başvuru derlemeleri

 Araç takımı 'nda belirtilen başvuru derlemeleri bir uygulama tasarlamanıza ve oluşturmanıza yardımcı olur. bu başvuru derlemeleri yalnızca belirli bir hedef derlemeyi etkinleştirmeyin, aynı zamanda Visual Studio ıde 'deki bileşenleri ve özellikleri hedefle uyumlu olanlarla kısıtlar. Daha fazla bilgi için bkz. [tasarım zamanında derlemeleri çözümleme](../msbuild/resolving-assemblies-at-design-time.md).

## <a name="configure-targets-and-tasks"></a>Hedefleri ve görevleri yapılandırma

 MSBuild hedeflerini ve görevleri, üzerinde çalışmakta olduğunuz sunucudan önemli ölçüde farklı olan bağlamların hedeflemesini sağlamak için MSBuild ile işlem dışı çalışacak şekilde yapılandırabilirsiniz.  örneğin, geliştirme bilgisayarı .NET Framework 4,5 ile 64 bit platformda çalışırken 32 bitlik bir .NET Framework 2,0 uygulamasını hedefleyebilirsiniz. Daha fazla bilgi için bkz. [hedefleri ve görevleri yapılandırma](../msbuild/configuring-targets-and-tasks.md).

## <a name="troubleshooting"></a>Sorun giderme

 Hedef bağlamın parçası olmayan bir derlemeye başvuru yapmayı denerseniz hatalarla karşılaşabilirsiniz. bu hatalar ve bunlarla ilgili daha fazla bilgi için bkz. [.NET Framework hedefleme hatalarını giderme](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).
