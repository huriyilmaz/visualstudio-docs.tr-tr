---
title: MSBuild Multitargeting Genel Bakış | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: eecbcd65-9fbc-4307-a321-46d3c3b79b12
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: af7649a75fbf3ded0cf5d09e9063b49f4fcab1b2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633336"
---
# <a name="msbuild-multitargeting-overview"></a>MSBuild çoklu hedeflemeye genel bakış

MSBuild'i kullanarak, .NET Framework'ün çeşitli sürümlerinden herhangi birinde ve çeşitli sistem platformlarından herhangi birinde çalışacak bir uygulama derleyebilirsiniz. Örneğin, 32 bit platformda .NET Framework 2.0 üzerinde çalışacak bir uygulama derleyebilir ve aynı uygulamayı 64 bit platformda .NET Framework 4.5'te çalışacak şekilde derleyebilirsiniz.

> [!IMPORTANT]
> "Çok hedefleme" adına rağmen, bir proje aynı anda yalnızca bir çerçeveyi ve yalnızca bir platformu hedefleyebilir.

 Bunlar, MSBuild hedeflemesinin özelliklerinden bazılarıdır:

- .NET Framework'ün önceki bir sürümünü hedefleyen bir uygulama geliştirebilirsiniz, örneğin, sürüm 2.0, 3.5 veya 4.

- .NET Framework dışında bir çerçeve hedefleyebilirsiniz, örneğin, Silverlight Framework.

- Hedef *çerçevenin*önceden tanımlanmış bir alt kümesi olan bir çerçeve profilini hedefleyebilirsiniz.

- .NET Framework'ün geçerli sürümü için bir hizmet paketi serbest bırakılırsa, bunu hedefleyebilirsiniz.

- MSBuild hedefleme, bir uygulamanın yalnızca hedeflenen çerçeve ve platformda kullanılabilen işlevselliği kullandığını garanti eder.

## <a name="target-framework-and-platform"></a>Hedef çerçeve ve platform

 *Hedef çerçeve,* bir projenin üzerinde çalışmak üzere inşa edilen .NET Framework sürümüdür ve *hedef platform,* projenin üzerinde çalışmak üzere inşa edilen sistem platformudur.  Örneğin, 802x86 işlemci ailesiyle (x86) uyumlu 32 bitlik bir platformda çalışacak bir .NET Framework 2.0 uygulamasını hedeflemek isteyebilirsiniz. Hedef çerçevesi ve hedef platformunun birleşimi *hedef bağlam*olarak bilinir. Daha fazla bilgi için [Hedef çerçevesi ve hedef platformuna](../msbuild/msbuild-target-framework-and-target-platform.md)bakın.

## <a name="toolset-toolsversion"></a>Araç Takımı (ToolsVersion)

 Araç Kümesi, uygulamayı oluşturmak için kullanılan araçları, görevleri ve hedefleri bir araya toplar. Araç *Kümesi, csc.exe* ve *vbc.exe*, ortak hedefler dosyası (*microsoft.common.targets*) ve ortak görevler dosyası (*microsoft.common.tasks)* gibi derleyicileri içerir. 4.5 Araç Kümesi ,NET Framework sürümleri 2.0, 3.0, 3.5, 4 ve 4.5'i hedeflemek için kullanılabilir. Ancak, 2.0 Araç Kümesi yalnızca .NET Framework sürüm 2.0'ı hedeflemek için kullanılabilir. Daha fazla bilgi için [Toolset (ToolsVersion) bakın.](../msbuild/msbuild-toolset-toolsversion.md)

## <a name="reference-assemblies"></a>Başvuru derlemeleri

 Araç Kümesi'nde belirtilen başvuru derlemeleri, bir uygulama tasarlamanıza ve oluşturmanıza yardımcı olur. Bu başvuru derlemeleri yalnızca belirli bir hedef oluşturmaya olanak sağlamakla kalmıyor, aynı zamanda Visual Studio IDE'deki bileşenleri ve özellikleri hedefle uyumlu olanlarla sınırlandırmaktadır. Daha fazla bilgi için tasarım [zamanında derlemeleri çöz'e](../msbuild/resolving-assemblies-at-design-time.md)bakın.

## <a name="configure-targets-and-tasks"></a>Hedefleri ve görevleri yapılandırma

 MSBuild hedeflerini ve görevlerini, üzerinde çalışan ından çok farklı bağlamları hedefleyebilmeniz için MSBuild ile işlem dışı çalışacak şekilde yapılandırabilirsiniz.  Örneğin, geliştirme bilgisayarı .NET Framework 4.5'e sahip 64 bit lik bir platformda çalışırken 32 bit, .NET Framework 2.0 uygulamasını hedefleyebilirsiniz. Daha fazla bilgi için [bkz.](../msbuild/configuring-targets-and-tasks.md)

## <a name="troubleshooting"></a>Sorun giderme

 Hedef bağlamın bir parçası olmayan bir derlemeye başvurmaya çalışırsanız hatalarla karşılaşabilirsiniz. Bu hatalar ve bunlar hakkında ne yapmanız hakkında daha fazla bilgi için [Sorun Giderme .NET Framework hedefleme hatalarına](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)bakın.
