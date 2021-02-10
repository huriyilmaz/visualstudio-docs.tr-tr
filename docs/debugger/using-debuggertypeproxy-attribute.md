---
title: DebuggerTypeProxy kullanarak özel tür görüntüle | Microsoft Docs
description: Bir tür için proxy (tek başına) belirtmek için bir DebuggerTypeProxyAttribute örneğini kullanın, türün hata ayıklayıcı penceresinde nasıl görüntüleneceğini değiştirin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2fdd0b67075a66663146d706d8f82e8c5d9f76e2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99940546"
---
# <a name="tell-the-debugger-what-type-to-show-using-debuggertypeproxy-attribute-c-visual-basic-ccli"></a>Hata ayıklayıcıya DebuggerTypeProxy özniteliği kullanarak hangi türün gösterileceğini söyleyin (C#, Visual Basic, C++/CLı)

<xref:System.Diagnostics.DebuggerTypeProxyAttribute> bir ara sunucu veya bir tür için tek başına belirtir ve türün hata ayıklayıcı penceresinde görüntülenme şeklini değiştirir. Proxy 'si olan bir değişkeni görüntülediğinizde, proxy, **ekranda** orijinal tür için temsil eder. Hata ayıklayıcı değişkeni penceresi yalnızca proxy türünün ortak üyelerini görüntüler. Özel Üyeler gösterilmez.

Bu öznitelik, öğesine uygulanabilir:

- Yapılar
- Sınıflar
- Bütünleştirilmiş Kodlar

> [!NOTE]
> Yerel kod için bu öznitelik yalnızca C++/CLı kodunda desteklenir.

Bir tür proxy sınıfı, proxy 'nin yerini alacak türün bağımsız değişkenini alan bir oluşturucuya sahip olmalıdır. Hata ayıklayıcı, hedef türün bir değişkenini görüntülemesi gereken her seferinde tür proxy sınıfının yeni bir örneğini oluşturur. Bu performans açısından olumsuz etkileri olabilir. Sonuç olarak, Kurucuda kesinlikle gerekli olandan daha fazla iş yapmanız gerekmez.

Performans cezalarını en aza indirmek için, ifade değerlendirici, tür Kullanıcı tarafından genişletilmediği takdirde, hata ayıklayıcı penceresindeki + simgesine tıklanmadığı veya ' nin kullanımı dışında, bu türün görüntüleme ara sunucusu üzerindeki öznitelikleri incelemez <xref:System.Diagnostics.DebuggerBrowsableAttribute> . Bu nedenle, öznitelikleri görüntüleme türüne yerleştirmemelisiniz. Öznitelikleri, görüntüleme türünün gövdesinde kullanılmalıdır ve kullanılması gerekir.

Tür proxy 'sinin, özniteliğin hedeflediği sınıf içinde özel bir iç içe sınıf olması iyi bir fikirdir. Bu, iç üyelere kolayca erişmesini sağlar.

<xref:System.Diagnostics.DebuggerTypeProxyAttribute> devralınabilir, bu nedenle bir temel sınıfta tür ara sunucusu belirtilmişse türetilmiş sınıflar kendi tür ara sunucusunu belirtmedikleri takdirde, bu türetilmiş sınıflar için de geçerlidir.

<xref:System.Diagnostics.DebuggerTypeProxyAttribute>Derleme düzeyinde kullanılırsa `Target` parametresi, proxy 'nin yerine geçecek türü belirtir.

Ve ile birlikte bu özniteliğin kullanımıyla ilgili bir örnek için <xref:System.Diagnostics.DebuggerDisplayAttribute> <xref:System.Diagnostics.DebuggerTypeProxyAttribute> , bkz.[DebuggerDisplay özniteliğini kullanma](../debugger/using-the-debuggerdisplay-attribute.md).

## <a name="using-generics-with-debuggertypeproxy"></a>DebuggerTypeProxy ile genel türler kullanma

Genel türler için destek sınırlıdır. C# için `DebuggerTypeProxy` yalnızca açık türleri destekler. Oluşturulmamış tür olarak da bilinen açık bir tür, tür parametrelerinin bağımsız değişkenleriyle örneklenmiş genel bir tür. Oluşturulan türler de denilen kapalı türler desteklenmez.

Açık bir tür için sözdizimi şöyle görünür:

`Namespace.TypeName<,>`

İçinde bir hedef olarak genel bir tür kullanırsanız `DebuggerTypeProxy` , bu söz dizimini kullanmanız gerekir. `DebuggerTypeProxy`Mekanizması sizin için tür parametrelerini algılar.

C# ' de açık ve kapalı türler hakkında daha fazla bilgi için bkz. [C# dil belirtimi](/dotnet/csharp/language-reference/language-specification), Bölüm 20.5.2 açık ve kapalı türler.

Visual Basic açık tür sözdizimine sahip olmadığından, Visual Basic aynı şeyi yapamayacağınız. Bunun yerine, açık tür adının bir dize gösterimini kullanmanız gerekir.

`"Namespace.TypeName'2"`

## <a name="see-also"></a>Ayrıca bkz.

- [DebuggerDisplay Özniteliğini Kullanma](../debugger/using-the-debuggerdisplay-attribute.md)
- [Yönetilen nesnelerin özel görünümlerini oluşturma](../debugger/create-custom-views-of-managed-objects.md)
- [Hata Ayıklayıcı Görüntü Öznitelikleriyle Hata Ayıklamayı Geliştirme](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)
