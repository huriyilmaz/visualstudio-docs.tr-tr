---
title: MSBuild Çoklu HedefLere Genel Bakış | Microsoft Docs
description: MSBuild'nin çeşitli sürümlerinden herhangi biri üzerinde ve çeşitli sistem platformlarından herhangi biri üzerinde .NET Framework derlemek için .NET Framework kullanmayı öğrenin.
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
ms.openlocfilehash: c137904db1e8b4caaeb71ee4a787122648554e0f
ms.sourcegitcommit: efe1d737fd660cc9183177914c18b0fd4e39ba8b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2021
ms.locfileid: "130208350"
---
# <a name="msbuild-multitargeting-overview"></a>MSBuild çoklu sürüm desteğine genel bakış

Bu MSBuild kullanarak, bir uygulamayı derlemenin çeşitli sürümlerinden herhangi biri üzerinde ve .NET Framework herhangi bir sistem platformunda çalıştıracak şekilde derleyebilirsiniz. Örneğin, 32 bitlik bir platformda .NET Framework 2.0'da çalıştıracak bir uygulama derler ve aynı uygulamayı 64 bitlik bir platformda .NET Framework 4.5 üzerinde çalıştıracak şekilde derlersiniz.

> [!IMPORTANT]
> "Çoklu hedef" adına rağmen, bir proje aynı anda yalnızca bir çerçeveyi ve yalnızca bir platformu hedefleyene kadar devam ediyor olabilir.

 Aşağıdakiler, MSBuild hedeflemenin özelliklerinden bazılarıdır:

- .NET Framework 2.0, 3.5 veya 4 gibi önceki bir sürümü hedef alan bir uygulama geliştirebilirsiniz.

- Örneğin Silverlight Framework gibi .NET Framework bir çerçeveyi hedefleysiniz.

- Hedef çerçevenin *önceden tanımlanmış* bir alt kümesi olan bir çerçeve profilini hedefleyebilirsiniz.

- Geçerli sürümü için bir hizmet paketi .NET Framework, hedefleyabilirsiniz.

- MSBuild, bir uygulamanın yalnızca hedeflenen çerçevede ve platformda kullanılabilen işlevleri kullandığını garantiler.

## <a name="target-framework-and-platform"></a>Hedef çerçeve ve platform

 Hedef *çerçeve,* bir .NET Framework üzerinde çalıştıracak şekilde, hedef *platform* ise projenin üzerinde çalıştıracak şekilde inşa edilen sistem platformudur.  Örneğin, 80x86 işlemci ailesi (x86) ile uyumlu bir 32 bit platform üzerinde çalıştırmak için bir .NET Framework 2.0 uygulamasını hedeflemek istiyor olabilir. Hedef çerçeve ve hedef platformun birleşimi hedef bağlam *olarak bilinir.* Daha fazla bilgi için [bkz. Hedef çerçeve ve hedef platform.](../msbuild/msbuild-target-framework-and-target-platform.md)

## <a name="toolset-toolsversion"></a>Araç Takımı (ToolsVersion)

 Araç Kümesi, uygulamayı oluşturmak için kullanılan araçları, görevleri ve hedefleri bir araya toplar. Araç Kümesi, *csc.exevevbc.exe* , ** ortak hedefler dosyası (*microsoft.common.targets*) ve ortak görevler dosyası (*microsoft.common.tasks*) gibi derleyicileri içerir. 4.5 Araç Seti, .NET Framework 2.0, 3.0, 3.5, 4 ve 4.5 sürümlerini hedeflemek için kullanılabilir. Ancak, 2.0 Araç Seti yalnızca 2.0 .NET Framework hedeflemek için kullanılabilir. Daha fazla bilgi için [bkz. Araç Kümesi (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md).

## <a name="reference-assemblies"></a>Başvuru derlemeleri

 Araç Kümesinde belirtilen başvuru derlemeleri bir uygulama tasarlamanıza ve derlemeye yardımcı olur. Bu başvuru derlemeleri yalnızca belirli bir hedef derlemeyi etkinleştirmekle birlikte, IDE'de Visual Studio ve özellikleri hedefle uyumlu olanlarla kısıtlar. Daha fazla bilgi için [bkz. Derlemeleri tasarım zamanında çözümleme.](../msbuild/resolving-assemblies-at-design-time.md)

## <a name="configure-targets-and-tasks"></a>Hedefleri ve görevleri yapılandırma

 MSBuild ile MSBuild ve görevleri, üzerinde çalıştırılandan çok daha farklı bağlamları hedeflemek için MSBuild ile işlem dışında olacak şekilde yapılandırabilirsiniz.  Örneğin, geliştirme bilgisayarı 4.5'e sahip 64 bit bir platformda çalışırken 32 bit, .NET Framework 2.0 .NET Framework hedefleyebilirsiniz. Daha fazla bilgi için [bkz. Hedefleri ve görevleri yapılandırma.](../msbuild/configure-tasks.md)

## <a name="troubleshooting"></a>Sorun giderme

 Hedef bağlamın parçası olan bir derlemeye başvurursanız hatalarla karşılaşabilirsiniz. Bu hatalar ve bunlar hakkında ne yapacakları hakkında daha fazla bilgi için bkz. .NET Framework [giderme.](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)
