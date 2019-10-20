---
title: '&lt;loc &gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <loc> JavaScript XML tag
- loc JavaScript XML tag
ms.assetid: 0d3349b6-4bdd-418f-bc11-73665305baae
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cf6016b2c12fd5ebe7cfb76c14c776508d99d2db
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651472"
---
# <a name="ltlocgt-javascript"></a>&lt;loc &gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yerelleştirilmiş IntelliSense bilgilerini sağlayan sepet dosyasının konumunu ve türünü belirtir.

## <a name="syntax"></a>Sözdizimi

```
<loc filename="filename"
    format="vsdoc|messagebundle" />
```

#### <a name="parameters"></a>Parametreler
 Isteğe bağlı `filename`. Bağımsız kültür için yerelleştirme bilgilerini içeren sepet dosyasının kök adı. Visual Studio yerelleştirme bilgilerini aradığında, bu dosyanın kültüre özgü bir sürümünü bulmaya çalışır. Örneğin, `filename` jQuery. xml ise, Visual Studio `<loc>` öğesini içeren. js dosyası ile aynı konumdaki doğru kültüre özgü klasörü (JA gibi) arar. Kültüre özgü bir klasör bulunursa, bir jQuery. xml dosyasının mevcut olup olmadığını denetler. Doğru dosyayı bulamazsa, bunun yerine yönetilen kaynak konum kurallarını kullanır. @No__t_0 varsayılan değeri, geçerli dosyanın adıdır, ancak. js yerine. xml uzantısıyla.

 Isteğe bağlı `format`. Yerelleştirme için kullanılan sepet dosyasının türü. Açık Ajax meta verileri tarafından tanımlanan ileti demeti kullanımını belirtmek için `messagebundle` kullanın. Önerilen biçim `messagebundle`. Ancak, bu biçim Microsoft Ajax veya. winmd dosyalarında desteklenmez. Microsoft Ajax ve Windows Çalışma Zamanı tarafından kullanılan standart .NET Framework yerelleştirme biçimini belirtmek için `vsdoc` kullanın. Bu öznitelik isteğe bağlıdır. Varsayılan biçimdir `vsdoc`.

## <a name="remarks"></a>Açıklamalar
 @No__t_0 öğesi, `<reference>` öğesiyle aynı bölümdeki dosyanın en üstünde yer almalıdır. @No__t_0 öğesi için kullanım kuralları `<reference>` öğesi ile aynıdır. Daha fazla bilgi için, [JavaScript IntelliSense](../ide/javascript-intellisense.md)'Teki "başvuru yönergeleri" bölümüne bakın.

 Visual Studio her. js dosyası için tek bir `<loc>` öğesini işler. Birden çok `<loc>` öğesi varsa, yalnızca tek bir `<loc>` öğesi kullanılır. Hangi `<loc>` öğesinin kullanılacağını belirlemek için davranış tanımlı değil.

 İleti paketi biçimini kullanırken, XML belge açıklamalarındaki `locid` özniteliğini kullanarak `name` öznitelik değerini belirtin.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, `<loc>` öğesinin messagedemeti biçimiyle nasıl kullanılacağını gösterir. Aşağıdaki XML 'i messageFilename. xml adlı bir dosyaya ekleyin ve dosyayı `filename` parametresinin açıklamasında belirtildiği gibi doğru kültüre özgü klasöre yerleştirin.

```
<?xml version="1.0" encoding="utf-8" ?>
<messagebundle>
  <msg name="1">A class that represents a rectangle</msg>
  <msg name="2">The height of a rectangle</msg>
  <msg name="3">The width of a rectangle</msg>
</messagebundle>

```

 Messagedemeti örneği için, projenizdeki bir JavaScript dosyasına aşağıdaki kodu ekleyin. @No__t_0 öğesi JavaScript dosyasındaki ilk satır olarak görünmelidir. Bu koddaki açıklamalar, varsa yerelleştirilmiş açıklamalarla değiştirileceğini caktır.

```javascript
/// <loc filename="messageFilename.xml" format="messagebundle"/>

function doSomething(a,b)
{
    /// <summary locid='1'>description</summary>
    /// <param name='a' locid='2'>parameter a description</param>
    /// <param name='b' locid='3'>parameter b description</param>
}

```

 Aşağıdaki örnek VSDoc biçimini kullanır. Aşağıdaki XML 'i scriptFilename. xml adlı bir dosyaya ekleyin ve dosyayı doğru kültüre özgü klasöre yerleştirin.

```
<?xml version="1.0" encoding="utf-8" ?>
<doc>
  <assembly>
    <name>Lights</name>
  </assembly>
  <members>
    <member name="M:illuminate">
      <summary>Activates a light. </summary>
      <param name='a'>The light to activate. </param>
    </member>
  </members>
</doc>

```

 VSDoc örneği için, projenizdeki bir JavaScript dosyasına aşağıdaki kodu ekleyin. Bu koddaki açıklamalar, varsa yerelleştirilmiş açıklamalarla değiştirileceğini caktır.

```javascript
/// <loc filename="scriptFilename.xml" format="vsdoc" />

function illuminate(a)
{
    /// <summary locid='M:illuminate'>description</summary>
    /// <param name='a' type='Number'>parameter a description</param>
}

```

## <a name="see-also"></a>Ayrıca Bkz.
 [XML Belge Açıklamaları](../ide/xml-documentation-comments-javascript.md)
