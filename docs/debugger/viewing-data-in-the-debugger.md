---
title: Hata ayıklayıcısında verilerin özel görünümlerini | Microsoft Docs
description: Hata ayıklayıcısında program durumunu incelemenin ve değiştirmenin Visual Studio öğrenin. Bunlar Otomatikler ve İzleme pencereleri, DataTips ve Görselleştiriciler'i içerir.
ms.custom: SEO-VS-2020
ms.date: 01/09/2019
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], inspecting programs
- debugger, viewing data
ms.assetid: 13e1105f-f987-402e-9108-ec6ac12be042
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 2ef14445d3a4197a61abb1a7dc6df61bfdf277eb
ms.sourcegitcommit: 965372ad0d75f015403c1af508080bf799914ce3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "135803069"
---
# <a name="create-custom-views-of-data-in-the-visual-studio-debugger-c-visual-basic-c"></a>Visual Studio hata ayıklayıcısında (C#, Visual Basic, C++) verilerin özel görünümlerini oluşturma

Hata [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ayıklayıcısı, program durumunu incelemek ve değiştirmek için birçok araç sağlar. Bu araçların çoğu yalnızca kesme modunda çalışır.

## <a name="create-custom-views-of-data-in-variable-windows-and-datatips"></a>Değişken pencerelerde ve DataTips'te verilerin özel görünümlerini oluşturma

 Otomatikler [ve İzleme pencereleri](../debugger/debugger-windows.md)gibi hata **ayıklayıcısı pencerelerinin** **çoğu** değişkenleri incelemenizi sağlar. C++ türlerinin, yönetilen nesnelerin ve kendi türlerinizi hata ayıklayıcısı değişken pencerelerinde ve [DataTips'te nasıl gösterebileceğinizi özelleştirebilirsiniz.](../debugger/view-data-values-in-data-tips-in-the-code-editor.md) Daha fazla bilgi için [bkz. C++ nesnelerinin özel görünümlerini oluşturma](../debugger/create-custom-views-of-native-objects.md) [ve Yönetilen nesnelerin özel görünümlerini oluşturma.](../debugger/create-custom-views-of-managed-objects.md)

## <a name="create-custom-visualizers"></a>Özel görselleştiriciler oluşturma

 Görselleştiriciler, bir nesnenin veya değişkenin içeriğini anlamlı bir şekilde görüntülemenizi sağlar. Hata Visual Studio görselleştirici, büyüteç ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "Görselleştirici simgesi") simgesini kullanarak açabilirsiniz farklı pencerelere başvurur. Örneğin, HTML görselleştiricisi bir HTML dizesinin tarayıcıda nasıl yorumlandır ve görüntülenebilir olduğunu gösterir. Görselleştiricilere DataTips, **İzleme** penceresi, Otomatikler **penceresi ve** Yereller **penceresinden erişebilirsiniz.** QuickWatch **iletişim** kutusu bir görselleştirici de sağlar. Daha fazla bilgi için [bkz. Özel görselleştiriciler oluşturma.](../debugger/create-custom-visualizers-of-data.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)
- [Komut penceresi](../ide/reference/command-window.md)
- [Hata ayıklayıcısı güvenliği](../debugger/debugger-security.md)
