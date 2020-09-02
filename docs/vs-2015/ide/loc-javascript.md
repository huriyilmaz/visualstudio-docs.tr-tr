---
title: '&lt;Loc &gt; (JavaScript) | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651472"
---
# <a name="ltlocgt-javascript"></a>&lt;Loc &gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yerelleştirilmiş IntelliSense bilgilerini sağlayan sepet dosyasının konumunu ve türünü belirtir.

## <a name="syntax"></a>Söz dizimi

```
<loc filename="filename"
    format="vsdoc|messagebundle" />
```

#### <a name="parameters"></a>Parametreler
 `filename` Seçim. Bağımsız kültür için yerelleştirme bilgilerini içeren sepet dosyasının kök adı. Visual Studio yerelleştirme bilgilerini aradığında, bu dosyanın kültüre özgü bir sürümünü bulmaya çalışır. Örneğin, jquery.xml ise `filename` , Visual Studio öğeyi içeren. js dosyası ile aynı konumdaki doğru kültüre özgü klasörü (ja gibi) arar `<loc>` . Kültüre özgü bir klasör bulunursa, içinde bir jquery.xml dosyasının bulunup bulunmadığını denetler. Doğru dosyayı bulamazsa, bunun yerine yönetilen kaynak konum kurallarını kullanır. Varsayılan değeri, `filename` . js yerine. xml uzantısıyla, geçerli dosyanın adıdır.

 `format` Seçim. Yerelleştirme için kullanılan sepet dosyasının türü. `messagebundle`Açık Ajax meta verileri tarafından tanımlanan ileti demeti kullanımını belirtmek için kullanın. `messagebundle` önerilen biçimdir. Ancak, bu biçim Microsoft Ajax veya. winmd dosyalarında desteklenmez. `vsdoc`Microsoft Ajax ve Windows çalışma zamanı tarafından kullanılan standart .NET Framework yerelleştirme biçimini belirtmek için kullanın. Bu öznitelik isteğe bağlıdır. `vsdoc` Varsayılan biçimdir.

## <a name="remarks"></a>Açıklamalar
 `<loc>`Öğesi, öğesiyle aynı bölümdeki dosyanın en üstünde yer almalıdır `<reference>` . Öğesi için kullanım kuralları `<loc>` öğesi ile aynıdır `<reference>` . Daha fazla bilgi için, [JavaScript IntelliSense](../ide/javascript-intellisense.md)'Teki "başvuru yönergeleri" bölümüne bakın.

 Visual Studio `<loc>` her. js dosyası için tek bir öğeyi işler. Birden çok `<loc>` öğe varsa, yalnızca tek bir `<loc>` öğe kullanılır. Kullanılacak öğeyi belirleme davranışı `<loc>` tanımlı değil.

 İleti paketi biçimini kullanırken, `locid` öznitelik değerini belirtmek IÇIN XML belge açıklamalarındaki özniteliğini kullanın `name` .

## <a name="example"></a>Örnek
 Aşağıdaki örnek, `<loc>` öğesinin messagedemeti biçimiyle nasıl kullanılacağını gösterir. Aşağıdaki XML 'i messageFilename.xml adlı bir dosyaya ekleyin ve dosyayı, parametrenin açıklamasında belirtildiği gibi doğru kültüre özgü klasöre yerleştirin `filename` .

```
<?xml version="1.0" encoding="utf-8" ?>
<messagebundle>
  <msg name="1">A class that represents a rectangle</msg>
  <msg name="2">The height of a rectangle</msg>
  <msg name="3">The width of a rectangle</msg>
</messagebundle>

```

 Messagedemeti örneği için, projenizdeki bir JavaScript dosyasına aşağıdaki kodu ekleyin. `<loc>`Öğe, JavaScript dosyasının ilk satırı olarak görünmelidir. Bu koddaki açıklamalar, varsa yerelleştirilmiş açıklamalarla değiştirileceğini caktır.

```javascript
/// <loc filename="messageFilename.xml" format="messagebundle"/>

function doSomething(a,b)
{
    /// <summary locid='1'>description</summary>
    /// <param name='a' locid='2'>parameter a description</param>
    /// <param name='b' locid='3'>parameter b description</param>
}

```

 Aşağıdaki örnek VSDoc biçimini kullanır. Aşağıdaki XML 'i scriptFilename.xml adlı bir dosyaya ekleyin ve dosyayı doğru kültüre özgü klasöre yerleştirin.

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
 [XML belge açıklamaları](../ide/xml-documentation-comments-javascript.md)
