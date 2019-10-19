---
title: DebuggerTypeProxy kullanarak özel tür görüntüle | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- attributes [C#], debugger
- DebuggerTypeProxyAttribute class
- DebuggerTypeProxy attribute
ms.assetid: 943f3bb1-993e-4800-a47e-0af78b063014
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 091619353adacaeb9c6996653ac64a0bcd84bb5c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72568960"
---
# <a name="tell-the-debugger-what-type-to-show-using-debuggertypeproxy-attribute-c-visual-basic-ccli"></a>Hata ayıklayıcıya DebuggerTypeProxy özniteliği (C#, Visual Basic, C++/CLI) kullanarak ne tür gösterileceğini söyleyin

<xref:System.Diagnostics.DebuggerTypeProxyAttribute>, bir ara sunucu veya bir tür için bağımsız olduğunu belirtir ve türün hata ayıklayıcı penceresinde görüntülenme şeklini değiştirir. Proxy 'si olan bir değişkeni görüntülediğinizde, proxy, **ekranda**orijinal tür için temsil eder. Hata ayıklayıcı değişkeni penceresi yalnızca proxy türünün ortak üyelerini görüntüler. Özel Üyeler gösterilmez.

Bu öznitelik, öğesine uygulanabilir:

- Yapılar
- Sınıflar
- Bütünleştirilmiş kodlar

> [!NOTE]
> Yerel kod için bu öznitelik yalnızca C++/CLI kodunda desteklenir.

Bir tür proxy sınıfı, proxy 'nin yerini alacak türün bağımsız değişkenini alan bir oluşturucuya sahip olmalıdır. Hata ayıklayıcı, hedef türün bir değişkenini görüntülemesi gereken her seferinde tür proxy sınıfının yeni bir örneğini oluşturur. Bu performans açısından olumsuz etkileri olabilir. Sonuç olarak, Kurucuda kesinlikle gerekli olandan daha fazla iş yapmanız gerekmez.

Performans cezalarını en aza indirmek için, ifade değerlendirici, tür Kullanıcı tarafından genişletilmediği takdirde, hata ayıklayıcı penceresinde + simgesine tıklanmadığı veya <xref:System.Diagnostics.DebuggerBrowsableAttribute> kullanımı dışında, türün görüntüleme proxy 'si üzerindeki öznitelikleri incelemez. Bu nedenle, öznitelikleri görüntüleme türüne yerleştirmemelisiniz. Öznitelikleri, görüntüleme türünün gövdesinde kullanılmalıdır ve kullanılması gerekir.

Tür proxy 'sinin, özniteliğin hedeflediği sınıf içinde özel bir iç içe sınıf olması iyi bir fikirdir. Bu, iç üyelere kolayca erişmesini sağlar.

<xref:System.Diagnostics.DebuggerTypeProxyAttribute> devralınabilir, bu nedenle bir temel sınıfta bir tür ara sunucusu belirtilmişse, bu türetilmiş sınıflar kendi tür ara sunucusunu belirtmedikleri takdirde, türetilmiş sınıflar için de geçerlidir.

Derleme düzeyinde <xref:System.Diagnostics.DebuggerTypeProxyAttribute> kullanılırsa, `Target` parametresi proxy 'nin yerine geçecek türü belirtir.

Bu özniteliğin <xref:System.Diagnostics.DebuggerDisplayAttribute> ve <xref:System.Diagnostics.DebuggerTypeProxyAttribute> birlikte nasıl kullanılacağına ilişkin bir örnek için, bkz.[DebuggerDisplay özniteliğini kullanma](../debugger/using-the-debuggerdisplay-attribute.md).

## <a name="using-generics-with-debuggertypeproxy"></a>DebuggerTypeProxy ile genel türler kullanma

Genel türler için destek sınırlıdır. İçin C#`DebuggerTypeProxy` yalnızca açık türleri destekler. Oluşturulmamış tür olarak da bilinen açık bir tür, tür parametrelerinin bağımsız değişkenleriyle örneklenmiş genel bir tür. Oluşturulan türler de denilen kapalı türler desteklenmez.

Açık bir tür için sözdizimi şöyle görünür:

`Namespace.TypeName<,>`

@No__t_0 bir hedef olarak genel bir tür kullanırsanız, bu söz dizimini kullanmanız gerekir. @No__t_0 mekanizması sizin için tür parametrelerini haller.

İçindeki C# açık ve kapalı türler hakkında daha fazla bilgi için, bkz. [ C# dil belirtimi](/dotnet/csharp/language-reference/language-specification), Bölüm 20.5.2 açık ve kapalı türler.

Visual Basic açık tür sözdizimine sahip olmadığından, Visual Basic aynı şeyi yapamayacağınız. Bunun yerine, açık tür adının bir dize gösterimini kullanmanız gerekir.

`"Namespace.TypeName'2"`

## <a name="see-also"></a>Ayrıca Bkz.

- [DebuggerDisplay Özniteliğini Kullanma](../debugger/using-the-debuggerdisplay-attribute.md)
- [Yönetilen nesnelerin özel görünümlerini oluşturma](../debugger/create-custom-views-of-managed-objects.md)
- [Hata Ayıklayıcı Görüntü Öznitelikleriyle Hata Ayıklamayı Geliştirme](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)
