---
title: Hata ayıklayıcıda verilerin özel görünümlerini oluşturma | Microsoft Docs
ms.date: 01/09/2019
ms.topic: conceptual
f1_keywords:
- vs.debug
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 63dc11736e92013719fcda2bae0ba9599a8835aa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72568994"
---
# <a name="create-custom-views-of-data-in-the-visual-studio-debugger-c-visual-basic-c"></a>Visual Studio hata ayıklayıcısında verilerin özel görünümlerini oluşturma (C#, Visual Basic, C++)

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Hata ayıklayıcı programınızın durumunu incelemek ve değiştirmek için birçok araç sağlar. Bu araçların çoğu yalnızca kesme modunda çalışır.

## <a name="create-custom-views-of-data-in-variable-windows-and-datatips"></a>Değişken Windows ve veri Ipuçlarında verilerin özel görünümlerini oluşturma

 **Oto** ve **Gözcü** pencereleri gibi [hata ayıklayıcı pencerelerinin](../debugger/debugger-windows.md)birçoğu, değişkenleri incelemenizi sağlar. C++ türlerinin, yönetilen nesnelerin ve kendi türlerinizin hata ayıklayıcı değişkeni penceresinde ve [veri ipuçlarında](../debugger/view-data-values-in-data-tips-in-the-code-editor.md)nasıl gösterileceğini özelleştirebilirsiniz. Daha fazla bilgi için bkz. [C++ nesnelerinin özel görünümlerini oluşturma](../debugger/create-custom-views-of-native-objects.md) ve [yönetilen nesnelerin özel görünümlerini oluşturma](../debugger/create-custom-views-of-managed-objects.md).

## <a name="create-custom-visualizers"></a>Özel Görselleştiriciler oluşturma

 Görselleştiriciler bir nesne veya değişkenin içeriğini anlamlı bir şekilde görüntülemenizi sağlar. Visual Studio hata ayıklayıcısında bir Görselleştirici, Büyüteç ![Visualizersimgesi](../debugger/media/dbg-tips-visualizer-icon.png "Görselleştirici simgesi") simgesini kullanarak açabileceğiniz farklı pencereler anlamına gelir. Örneğin, HTML Görselleştirici bir HTML dizesinin bir tarayıcıda nasıl yorumlanıp görüntüleneceğini gösterir. Görsel öğelere veri Ipuçları, **Gözcü** penceresi, **oto** penceresi ve **Yerel öğeler** penceresi aracılığıyla erişebilirsiniz. **QuickWatch** iletişim kutusu ayrıca bir Görselleştirici sağlar. Daha fazla bilgi için bkz. [özel Görselleştiriciler oluşturma](../debugger/create-custom-visualizers-of-data.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)
- [Komut penceresi](../ide/reference/command-window.md)
- [Hata ayıklayıcı güvenliği](../debugger/debugger-security.md)
