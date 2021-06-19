---
title: DebuggerTypeProxy kullanarak özel türü | Microsoft Docs
description: Bir tür için proxy (bekleme) belirtmek için DebuggerTypeProxyAttribute örneğini kullanarak türün hata ayıklayıcı pencerelerde nasıl görüntülendiğinden emin olmak için kullanın.
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
ms.openlocfilehash: 532850f8bb4ac6198481188c2a57a8db15a13873
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389286"
---
# <a name="tell-the-debugger-what-type-to-show-using-debuggertypeproxy-attribute-c-visual-basic-ccli"></a>Hata ayıklayıcısına DebuggerTypeProxy Özniteliği (C#, Visual Basic, C++/CLI) kullanarak hangi türü göster

<xref:System.Diagnostics.DebuggerTypeProxyAttribute> bir tür için ara sunucu veya beklemeyi belirtir ve türün hata ayıklayıcı pencerelerde görüntülenme yolunu değiştirir. Proxy'si olan bir değişkeni görüntüleniyorsa, ara sunucu, görüntüde özgün türün içinde **yer amaktadır.** Hata ayıklayıcısı değişken penceresi yalnızca ara sunucu türünün ortak üyelerini görüntüler. Özel üyeler görüntülenmez.

Bu öznitelik şu özelliklere uygulanabilir:

- Yapılar
- Sınıflar
- Bütünleştirilmiş Kodlar

> [!NOTE]
> Yerel kod için bu öznitelik yalnızca C++/CLI kodunda de destekler.

Tür proxy sınıfı, proxy'nin değiştirecek türde bir bağımsız değişken alan bir oluşturucuya sahip olması gerekir. Hata ayıklayıcısı, hedef türün bir değişkenini görüntülemesi gereken her durumda proxy sınıfının yeni bir örneğini oluşturur. Bunun performans üzerinde etkileri olabilir. Sonuç olarak, oluşturucuda kesinlikle gerekli olandan daha fazla iş yapmamalıdır.

Performans cezalarını en aza indirmek için ifade değerlendiricisi, tür, hata ayıklayıcı penceresinde + simgesine tıklayarak veya kullanarak genişletildikçe türün görünen proxy'sinde öznitelikleri <xref:System.Diagnostics.DebuggerBrowsableAttribute> incelemez. Bu nedenle, görüntüleme türünün kendisine öznitelikler yer değil. Öznitelikler, görüntüleme türünün gövdesinde kullanılabilir ve kullanılmalıdır.

Tür ara sunucusunun özniteliğin hedefle olduğu sınıf içinde özel bir iç içe geçmiş sınıf olması iyi bir fikirdir. Bu, dahili üyelere kolayca erişmesine olanak sağlar.

<xref:System.Diagnostics.DebuggerTypeProxyAttribute> devralınabilir; bu nedenle, bir temel sınıfta tür proxy'si belirtilirse, türetilmiş sınıflar kendi tür proxy'lerini belirtmediği sürece türetilen sınıflar için geçerli olur.

eğer <xref:System.Diagnostics.DebuggerTypeProxyAttribute> derleme düzeyinde kullanılırsa, `Target` parametresi proxy'nin değiştirecek türünü belirtir.

Bu özniteliği ve ile birlikte kullanma örneği için <xref:System.Diagnostics.DebuggerDisplayAttribute> <xref:System.Diagnostics.DebuggerTypeProxyAttribute> [bkz. Using the DebuggerDisplay Attribute](../debugger/using-the-debuggerdisplay-attribute.md).

## <a name="using-generics-with-debuggertypeproxy"></a>DebuggerTypeProxy ile Genel Türleri Kullanma

Genel tür desteği sınırlıdır. C# için yalnızca `DebuggerTypeProxy` açık türleri destekler. Tanınmayan tür olarak da adlandırılan açık tür, tür parametreleri için bağımsız değişkenlerle örneği olmayan genel bir tür olur. Oluşturulmuş türler olarak da adlandırılan kapalı türler desteklenmiyor.

Açık bir türün söz dizimi şöyledir:

`Namespace.TypeName<,>`

içinde hedef olarak genel bir tür `DebuggerTypeProxy` kullanıyorsanız, bu söz dizimini kullansanız gerekir. Mekanizma, `DebuggerTypeProxy` tür parametrelerini sizin için çıkartır.

C# dilinde açık ve kapalı türler hakkında daha fazla bilgi için [C# Dil](/dotnet/csharp/language-reference/language-specification)Belirtimi , bölüm 20.5.2 Açık ve kapalı türler bölümüne bakın.

Visual Basic açık tür söz dizimi yoksa, aynı şeyi Visual Basic. Bunun yerine, açık tür adının dize gösterimini kullan gerekir.

`"Namespace.TypeName'2"`

## <a name="see-also"></a>Ayrıca bkz.

- [DebuggerDisplay Özniteliğini Kullanma](../debugger/using-the-debuggerdisplay-attribute.md)
- [Yönetilen nesnelerin özel görünümlerini oluşturma](../debugger/create-custom-views-of-managed-objects.md)
- [Hata Ayıklayıcı Görüntü Öznitelikleriyle Hata Ayıklamayı Geliştirme](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)
