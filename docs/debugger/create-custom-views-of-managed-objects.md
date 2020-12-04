---
title: Yönetilen nesnelerin özel görünümlerini oluşturma | Microsoft Docs
description: Visual Studio hata ayıklayıcı, verileri değişken penceresinde görüntüler. Veri türlerinin (özel türler dahil) nasıl görüntüleneceğini özelleştirmeyi öğrenin.
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
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: c2248a361837f664b0f78acfe61f6d7588f5258b
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2020
ms.locfileid: "96560219"
---
# <a name="create-custom-views-of-managed-objects-c-visual-basic-f-ccli"></a>Yönetilen nesnelerin özel görünümlerini oluşturma (C#, Visual Basic, F #, C++/CLı)
Visual Studio 'Nun veri türlerini hata ayıklayıcı değişken pencerelerinin gösterdiği şekilde özelleştirebilirsiniz.

## <a name="attributes"></a>Öznitelikler

C#, Visual Basic, F # ve c++ (yalnızca c++/CLI) içinde,, ve kullanarak özel verilere yönelik genişletmeleri ekleyebilirsiniz <xref:System.Diagnostics.DebuggerTypeProxyAttribute> <xref:System.Diagnostics.DebuggerDisplayAttribute> <xref:System.Diagnostics.DebuggerBrowsableAttribute> .

.NET Framework 2,0 kodunda, Visual Basic Debuggergözatılabilir özniteliğini desteklemez. Bu sınırlama, .NET 'in daha yeni sürümlerinde kaldırılmıştır.

## <a name="visualizers"></a>Görselleştiriciler

Yönetilen herhangi bir veri türünü göstermek için bir Görselleştirici yazabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: Görselleştirici Yazma](create-custom-visualizers-of-data.md).

> [!NOTE]
> C++ kodu için, [hata ayıklayıcıda c++ nesnelerinin özel görünümlerini oluşturma](create-custom-views-of-native-objects.md)bölümünde açıklandığı gibi Natvis çerçevesini kullanarak özel veri türü genişletmeleri ekleyebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Hata ayıklayıcıya DebuggerDisplay özniteliğini kullanarak neyin gösterileceğini söyleyin](../debugger/using-the-debuggerdisplay-attribute.md)
- [Hata ayıklayıcıya DebuggerTypeProxy özniteliği kullanılarak hangi türün gösterileceğini söyleyin](../debugger/using-debuggertypeproxy-attribute.md)
- [İzleme ve Hızlı İzleme Pencereleri](../debugger/watch-and-quickwatch-windows.md)
- [Hata Ayıklayıcı Görüntü Öznitelikleriyle Hata Ayıklamayı Geliştirme](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)
