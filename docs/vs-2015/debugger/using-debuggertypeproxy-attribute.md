---
title: DebuggerTypeProxy özniteliğini kullanma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- attributes [C#], debugger
- DebuggerTypeProxyAttribute class
- DebuggerTypeProxy attribute
ms.assetid: 943f3bb1-993e-4800-a47e-0af78b063014
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f6e349dd5bea4e0d89c31864960a5438d1e2b13f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65684081"
---
# <a name="using-debuggertypeproxy-attribute"></a>DebuggerTypeProxy Özniteliğini Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DebuggerTypeProxyAttribute] (assetId: ı/t: System. Diagnostics. DebuggerTypeProxyAttribute? qualifyHint = false&oto Upgrade = true) bir tür için proxy veya tek bir değer belirtir ve türün hata ayıklayıcı penceresinde görüntülenme şeklini değiştirir. Proxy 'si olan bir değişkeni görüntülediğinizde, proxy, **ekranda**orijinal tür için temsil eder. Hata ayıklayıcı değişkeni penceresi yalnızca proxy türünün ortak üyelerini görüntüler. Özel Üyeler gösterilmez.  
  
 Bu öznitelik, öğesine uygulanabilir:  
  
- Yapılar  
  
- Sınıflar  
  
- Bütünleştirilmiş Kodlar  
  
  Bir tür proxy sınıfı, proxy 'nin yerini alacak türün bağımsız değişkenini alan bir oluşturucuya sahip olmalıdır. Hata ayıklayıcı, hedef türün bir değişkenini görüntülemesi gereken her seferinde tür proxy sınıfının yeni bir örneğini oluşturur. Bu performans açısından olumsuz etkileri olabilir. Sonuç olarak, Kurucuda kesinlikle gerekli olandan daha fazla iş yapmanız gerekmez.  
  
  Performans cezalarını en aza indirmek için, ifade değerlendirici, tür Kullanıcı tarafından genişletilmediği takdirde, hata ayıklayıcı penceresindeki + simgesine tıklanmadığı veya ' nin kullanımı dışında, bu türün görüntüleme ara sunucusu üzerindeki öznitelikleri incelemez <xref:System.Diagnostics.DebuggerBrowsableAttribute> . Bu nedenle, öznitelikleri görüntüleme türüne yerleştirmemelisiniz. Öznitelikleri, görüntüleme türünün gövdesinde kullanılmalıdır ve kullanılması gerekir.  
  
  Tür proxy 'sinin, özniteliğin hedeflediği sınıf içinde özel bir iç içe sınıf olması iyi bir fikirdir. Bu, iç üyelere kolayca erişmesini sağlar.  
  
  <xref:System.Diagnostics.DebuggerTypeProxyAttribute>Derleme düzeyinde kullanılırsa `Target` parametresi, proxy 'nin yerine geçecek türü belirtir.  
  
  Ve ile birlikte bu özniteliğin kullanımıyla ilgili bir örnek için <xref:System.Diagnostics.DebuggerDisplayAttribute> <xref:System.Diagnostics.DebuggerTypeProxyAttribute> , bkz.[DebuggerDisplay özniteliğini kullanma](../debugger/using-the-debuggerdisplay-attribute.md).  
  
## <a name="using-generics-with-debuggertypeproxy"></a>DebuggerTypeProxy ile genel türler kullanma  
 Genel türler için destek sınırlıdır. C# için `DebuggerTypeProxy` yalnızca açık türleri destekler. Oluşturulmamış tür olarak da bilinen açık bir tür, tür parametrelerinin bağımsız değişkenleriyle örneklenmiş genel bir tür. Oluşturulan türler de denilen kapalı türler desteklenmez.  
  
 Açık bir tür için sözdizimi şöyle görünür:  
  
 `Namespace.TypeName<,>`  
  
 İçinde bir hedef olarak genel bir tür kullanırsanız `DebuggerTypeProxy` , bu söz dizimini kullanmanız gerekir. `DebuggerTypeProxy`Mekanizması sizin için tür parametrelerini algılar.  
  
 C# ' de açık ve kapalı türler hakkında daha fazla bilgi için bkz. [C# dil belirtimi](https://msdn.microsoft.com/library/e5d5a5cc-636b-4bff-b9c8-a8edc6207c22), Bölüm 20.5.2 açık ve kapalı türler.  
  
 Visual Basic açık tür sözdizimine sahip olmadığından, Visual Basic aynı şeyi yapamayacağınız. Bunun yerine, açık tür adının bir dize gösterimini kullanmanız gerekir.  
  
 `"Namespace.TypeName'2"`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DebuggerDisplay özniteliğini kullanma](../debugger/using-the-debuggerdisplay-attribute.md)   
  [Hata Ayıklayıcı Görüntü Öznitelikleriyle Hata Ayıklamayı Geliştirme](https://msdn.microsoft.com/library/72bb7aa9-459b-42c4-9163-9312fab4c410)
