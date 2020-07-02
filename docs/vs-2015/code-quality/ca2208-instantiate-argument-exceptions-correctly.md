---
title: 'CA2208: bağımsız değişken özel durumlarını doğru örnekleyin | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2208
- InstantiateArgumentExceptionsCorrectly
helpviewer_keywords:
- InstantiateArgumentExceptionsCorrectly
- CA2208
ms.assetid: e2a48939-d9fa-478c-b2f9-3bdbce07dff7
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 6a63ebb7f3946926864c4dd882c281b5dcd7c6c5
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85535843"
---
# <a name="ca2208-instantiate-argument-exceptions-correctly"></a>CA2208: Bağımsız değişken özel durumlarını doğru örnekleyin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|InstantiateArgumentExceptionsCorrectly|
|CheckId|CA2208|
|Kategori|Microsoft. Usage|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni
 Olası nedenler aşağıdaki durumları içerir:

- Bir özel durum türünün varsayılan (parametresiz) oluşturucusuna bir çağrı yapılır veya [System. ArgumentException] öğesinden türetilir (<!-- TODO: review code entity reference <xref:assetId:///System.ArgumentException?qualifyHint=True&amp;autoUpgrade=True>  -->).

- Yanlış dize bağımsız değişkeni, veya [System. ArgumentException.] öğesinden türetilen bir özel durum türünün parametreli oluşturucusuna geçirilir (<!-- TODO: review code entity reference <xref:assetId:///System.ArgumentException.?qualifyHint=True&amp;autoUpgrade=True>  -->)

## <a name="rule-description"></a>Kural Tanımı
 Varsayılan oluşturucuyu çağırmak yerine, daha anlamlı bir özel durum iletisi sağlanmasını sağlayan Oluşturucu aşırı yüklemelerinin birini çağırın. Özel durum iletisi, geliştiriciyi hedeflemelidir ve hata koşulunu açıkça açıklamalı ve özel durumu nasıl düzeltebileceğiniz veya kaçınmalıdır.

 Ve türetilmiş türlerindeki bir ve iki dize Oluşturucusu imzaları <xref:System.ArgumentException> ve parametreleri açısından tutarlı değildir `message` `paramName` . Bu oluşturucuların doğru dize bağımsız değişkenleriyle çağrıldığından emin olun. İmzalar aşağıdaki gibidir:

 <xref:System.ArgumentException>(dize `message` )

 <xref:System.ArgumentException>(dize `message` , dize `paramName` )

 <xref:System.ArgumentNullException>(dize `paramName` )

 <xref:System.ArgumentNullException>(dize `paramName` , dize `message` )

 <xref:System.ArgumentOutOfRangeException>(dize `paramName` )

 <xref:System.ArgumentOutOfRangeException>(dize `paramName` , dize `message` )

 <xref:System.DuplicateWaitObjectException>(dize `parameterName` )

 <xref:System.DuplicateWaitObjectException>(dize `parameterName` , dize `message` )

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için ileti, parametre adı veya her ikisini de alan bir Oluşturucu çağırın ve bağımsız değişkenlerin Çağrılmakta olan tür için uygun olduğundan emin olun <xref:System.ArgumentException> .

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Yalnızca parametreli bir oluşturucunun doğru dize bağımsız değişkenleriyle çağrılması durumunda bu kuraldan bir uyarının gösterilmemesi güvenlidir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bir ArgumentNullException türünün bir örneğini yanlış örnekleyen bir oluşturucuyu gösterir.

 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/cpp/FxCop.Usage.InheritedPublic.cpp#1)]
 [!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/cs/FxCop.Usage.InheritedPublic.cs#1)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/vb/FxCop.Usage.InstantiateArgumentExceptionsCorrectly.vb#1)]

## <a name="example"></a>Örnek
 Aşağıdaki örnek, Oluşturucu bağımsız değişkenlerini değiştirerek yukarıdaki ihlalin düzeltir.

 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/cpp/FxCop.Usage.InheritedPublic.cpp#2)]
 [!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/cs/FxCop.Usage.InheritedPublic.cs#2)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/vb/FxCop.Usage.InstantiateArgumentExceptionsCorrectly.vb#2)]
