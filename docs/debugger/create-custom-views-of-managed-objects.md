---
title: Yönetilen nesnelerin özel görünümlerini oluşturma | Microsoft Docs
description: Visual Studio hata ayıklayıcı verileri değişken penceresinde görüntüler. Veri türlerinin (özel türler dahil) nasıl görüntüleneceğini özelleştirmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 01/08/2019
ms.topic: conceptual
f1_keywords:
- vs.debug.data.elements
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- data types, custom
- custom data types
- managed code, custom data types
- autoexp.dat file
- mcee_cs.dat file
- debugger, expanding data types
- mcee_mc.dat file
ms.assetid: 9969e9b2-9008-4729-8a14-0d6deaa61576
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- dotnet
ms.openlocfilehash: 0a45b905e085a703056fe88f7513a9ed299324de699a9695eaffab97e7dc586e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121345848"
---
# <a name="create-custom-views-of-managed-objects-c-visual-basic-f-ccli"></a>yönetilen nesnelerin özel görünümlerini oluşturma (C#, Visual Basic, F #, C++/clı)
Visual Studio hata ayıklayıcı değişken pencerelerinin veri türlerini görüntüleme biçimini özelleştirebilirsiniz.

## <a name="attributes"></a>Öznitelikler

C#, Visual Basic, F # ve c++ (yalnızca c++/clı) içinde,, ve kullanarak özel verilere yönelik genişletmeleri ekleyebilirsiniz <xref:System.Diagnostics.DebuggerTypeProxyAttribute> <xref:System.Diagnostics.DebuggerDisplayAttribute> <xref:System.Diagnostics.DebuggerBrowsableAttribute> .

.NET Framework 2,0 kodunda, Visual Basic debuggergözatılabilir özniteliğini desteklemez. Bu sınırlama, .NET 'in daha yeni sürümlerinde kaldırılmıştır.

## <a name="visualizers"></a>Görselleştiriciler

Yönetilen herhangi bir veri türünü göstermek için bir Görselleştirici yazabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: Görselleştirici Yazma](create-custom-visualizers-of-data.md).

> [!NOTE]
> C++ kodu için, [hata ayıklayıcıda c++ nesnelerinin özel görünümlerini oluşturma](create-custom-views-of-native-objects.md)bölümünde açıklandığı gibi Natvis çerçevesini kullanarak özel veri türü genişletmeleri ekleyebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Hata ayıklayıcıya DebuggerDisplay özniteliğini kullanarak neyin gösterileceğini söyleyin](../debugger/using-the-debuggerdisplay-attribute.md)
- [Hata ayıklayıcıya DebuggerTypeProxy özniteliği kullanılarak hangi türün gösterileceğini söyleyin](../debugger/using-debuggertypeproxy-attribute.md)
- [İzleme ve Hızlı İzleme Pencereleri](../debugger/watch-and-quickwatch-windows.md)
- [Hata Ayıklayıcı Görüntü Öznitelikleriyle Hata Ayıklamayı Geliştirme](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)
