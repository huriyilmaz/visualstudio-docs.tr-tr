---
title: Yönetilen nesnelerin özel görünümlerini oluşturma | Microsoft Docs
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
ms.openlocfilehash: 196ba13b95245b8c42e6d946572665792f71346d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745635"
---
# <a name="create-custom-views-of-managed-objects-c-visual-basic-f-ccli"></a>Yönetilen nesnelerin özel görünümlerini oluşturma (C#, Visual Basic, F#, C++/CLI)
Visual Studio 'Nun veri türlerini hata ayıklayıcı değişken pencerelerinin gösterdiği şekilde özelleştirebilirsiniz.

## <a name="attributes"></a>Öznitelikler

İçinde C#, Visual Basic, F#ve C++ (C++yalnızca/CLI kodu), <xref:System.Diagnostics.DebuggerTypeProxyAttribute>, <xref:System.Diagnostics.DebuggerDisplayAttribute> ve <xref:System.Diagnostics.DebuggerBrowsableAttribute> kullanarak özel verilere yönelik genişletmeleri ekleyebilirsiniz.

.NET Framework 2,0 kodunda, Visual Basic Debuggergözatılabilir özniteliğini desteklemez. Bu sınırlama, .NET 'in daha yeni sürümlerinde kaldırılmıştır.

## <a name="visualizers"></a>Görselleştiriciler

Yönetilen herhangi bir veri türünü göstermek için bir Görselleştirici yazabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: Görselleştirici Yazma](/visualstudio/debugger/create-custom-visualizers-of-data).

> [!NOTE]
> Kod C++ için, [hata ayıklayıcıdaki C++ nesnelerin özel görünümlerini oluşturma](/visualstudio/debugger/create-custom-views-of-native-objects)bölümünde açıklandığı gibi Natvis çerçevesini kullanarak özel veri türü genişletmeleri ekleyebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Hata ayıklayıcıya DebuggerDisplay özniteliğini kullanarak neyin gösterileceğini söyleyin](../debugger/using-the-debuggerdisplay-attribute.md)
- [Hata ayıklayıcıya DebuggerTypeProxy özniteliği kullanılarak hangi türün gösterileceğini söyleyin](../debugger/using-debuggertypeproxy-attribute.md)
- [İzleme ve Hızlı İzleme Pencereleri](../debugger/watch-and-quickwatch-windows.md)
- [Hata Ayıklayıcı Görüntü Öznitelikleriyle Hata Ayıklamayı Geliştirme](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)
