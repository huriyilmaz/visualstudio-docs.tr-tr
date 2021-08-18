---
title: Yönetilen nesnelerin özel görünümlerini oluşturma | Microsoft Docs
description: Visual Studio ayıklayıcısı verileri değişken pencerelerde görüntüler. Veri türlerinin (özel türler dahil) nasıl görüntülendiğinden nasıl özelleştirebileceğinizi öğrenin.
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
ms.openlocfilehash: 327e8d74120555a4a121775f79b8ac5afe923f77
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122052440"
---
# <a name="create-custom-views-of-managed-objects-c-visual-basic-f-ccli"></a>Yönetilen nesnelerin özel görünümlerini oluşturma (C#, Visual Basic, F#, C++/CLI)
Hata ayıklayıcısı değişken Visual Studio veri türlerini görüntüleme yolunu özelleştirebilirsiniz.

## <a name="attributes"></a>Öznitelikler

C#, Visual Basic, F# ve C++ (yalnızca C++/CLI kodu), , ve kullanarak özel veriler için <xref:System.Diagnostics.DebuggerTypeProxyAttribute> <xref:System.Diagnostics.DebuggerDisplayAttribute> genişletmeler <xref:System.Diagnostics.DebuggerBrowsableAttribute> ebilirsiniz.

2.NET Framework 2.0 kodunda Visual Basic DebuggerBrowsable özniteliğini desteklemez. Bu sınırlama .NET'in daha yeni sürümlerinde kaldırılmıştır.

## <a name="visualizers"></a>Görselleştiriciler

Herhangi bir yönetilen veri türünü görüntülemek için görselleştirici yazabilirsiniz. Daha fazla bilgi için, [bkz. How to: Write a Visualizer](create-custom-visualizers-of-data.md).

> [!NOTE]
> C++ kodu için, hata ayıklayıcısında C++ nesnelerinin özel görünümlerini oluşturma konusunda açıklandığı gibi Natvis çerçevesini kullanarak [özel veri türü genişletmeleri ebilirsiniz.](create-custom-views-of-native-objects.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Hata ayıklayıcısına DebuggerDisplay Özniteliğini kullanarak ne göster göster göster](../debugger/using-the-debuggerdisplay-attribute.md)
- [Hata ayıklayıcısına DebuggerTypeProxy Özniteliğini kullanarak hangi türü göster göster](../debugger/using-debuggertypeproxy-attribute.md)
- [İzleme ve Hızlı İzleme Pencereleri](../debugger/watch-and-quickwatch-windows.md)
- [Hata Ayıklayıcı Görüntü Öznitelikleriyle Hata Ayıklamayı Geliştirme](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)
