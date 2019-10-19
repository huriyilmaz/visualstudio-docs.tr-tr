---
title: Yönetilen nesnelerin özel görünümlerini oluşturma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.data.elements
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- data types [C#], custom
- custom data types
- managed code, custom data types
- autoexp.dat file
- mcee_cs.dat file
- debugger, expanding data types
- mcee_mc.dat file
ms.assetid: 9969e9b2-9008-4729-8a14-0d6deaa61576
caps.latest.revision: 37
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cb5b56404c7ddc99b7999b47cf3c2a899f915efd
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72578057"
---
# <a name="create-custom-views-of-managed-objects"></a>Yönetilen Nesnelerin Özel Görünümlerini Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 'Nun veri türlerini hata ayıklayıcı değişken pencerelerinin gösterdiği şekilde özelleştirebilirsiniz.  
  
## <a name="attributes"></a>Öznitelikler  
 C# Ve Visual Basic, <xref:System.Diagnostics.DebuggerTypeProxyAttribute>, <xref:System.Diagnostics.DebuggerDisplayAttribute> ve <xref:System.Diagnostics.DebuggerBrowsableAttribute> kullanarak özel verilere yönelik genişletmeleri ekleyebilirsiniz.  
  
 @No__t_0 kod içinde, Visual Basic Debuggergözatılabilen özniteliğini desteklemez. Bu sınırlama, .NET Framework daha yeni sürümlerinde kaldırılır.  
  
## <a name="visualizers"></a>Görselleştiriciler  
 Yönetilen herhangi bir veri türünü göstermek için bir Görselleştirici yazabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: Görselleştirici Yazma](../debugger/how-to-write-a-visualizer.md).  
  
## <a name="native-code"></a>Yerel kod  
 Yerel kod için, Program Files\Microsoft Visual Studio 11.0 \ Common7\Packages\Debugger dizininde bulunan oto. dat dosyasına özel veri türü genişletmeleri ekleyebilirsiniz. @No__t_0 kuralların nasıl yazılacağı hakkındaki yönergeler dosyanın kendisindedir.  
  
> [!CAUTION]
> Bu dosyanın yapısı ve oto exp kurallarının sözdizimi, Visual Studio 'nun bir sürümünden sonrakine değişebilir.  
  
 Yerel tür görünümleri, bir ifade değerlendirici eklentisi yazılarak da özelleştirilebilir. Daha fazla bilgi için bkz. [Eeaddin örneği: hata ayıklama Ifade değerlendirici eklentisi](https://msdn.microsoft.com/d4f6b068-c812-45bc-9ec0-7e0363c4bb9e).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DebuggerTypeProxy öznitelik   kullanma](../debugger/using-debuggertypeproxy-attribute.md)  
 [DebuggerDisplay özniteliğini kullanma](../debugger/using-the-debuggerdisplay-attribute.md)    
 [Windows   izleme ve QuickWatch](../debugger/watch-and-quickwatch-windows.md)  
 [Hata Ayıklayıcı Görüntü Öznitelikleriyle Hata Ayıklamayı Geliştirme](https://msdn.microsoft.com/library/72bb7aa9-459b-42c4-9163-9312fab4c410)
