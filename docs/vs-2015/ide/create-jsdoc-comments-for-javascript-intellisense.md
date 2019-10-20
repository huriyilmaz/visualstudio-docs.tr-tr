---
title: JavaScript IntelliSense için JSDoc açıklamaları oluşturma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: a0dadc81-3755-4a47-bcee-c1010819ff2a
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b974f3450b88ab22e58e284881f270c1b3d72298
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72619269"
---
# <a name="create-jsdoc-comments-for-javascript-intellisense"></a>JavaScript IntelliSense için JSDoc Açıklamaları Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 'da IntelliSense, standart JSDoc açıklamalarını kullanarak bir betiğe eklediğiniz bilgileri görüntüler. İşlevler, alanlar ve değişkenler gibi kod öğeleri hakkında bilgi sağlamak için JSDoc açıklamalarını kullanabilirsiniz.

## <a name="jsdoc-comment-tags"></a>JSDoc açıklama etiketleri
 Aşağıdaki standart JSDoc açıklama etiketleri IntelliSense tarafından kodunuz hakkında bilgi göstermek için kullanılır.

|  JSDoc etiketi   |                       Sözdizimi                        |                                                     Notlar                                                      |
|--------------|-----------------------------------------------------|----------------------------------------------------------------------------------------------------------------|
| @deprecated  |              @deprecated *açıklaması*              |                                   Kullanım dışı bırakılan bir işlevi veya yöntemi belirtir.                                   |
| @description |             @description *açıklaması*              |                              Bir işlev veya yöntem için açıklama belirtir.                               |
|    @param    | @param {*Type*} *ParameterName*<em>açıklaması</em> | Bir işlev veya metot içindeki bir parametre için bilgi belirtir.<br /><br /> TypeScript Ayrıca @paramTag destekler. |
|  @property   |          @property {*Type*} *PropertyName*          |   Bir nesne için tanımlanmış bir alan veya üye için bir açıklama dahil olmak üzere bilgileri belirtir.    |
|   @returns   |                  @returns {*Type*}                  |           Bir dönüş değeri belirtir.<br /><br /> TypeScript için @returns yerine @returnType kullanın.           |
|   @summary   |               @summary *açıklaması*                |                   Bir işlev veya yöntem için açıklamayı belirtir (@description ile aynı).                   |
|    @type     |                   @type {*Type*}                    |                                Bir sabit veya değişken türünü belirtir.                                |
|   @typedef   |         @typedef {*Type*} *customtypename*          |                                            Özel bir tür belirtir.                                            |

### <a name="examples"></a>Örnekler
 Aşağıdaki örnek, `getArea` adlı bir işlev için @description, @param ve @return JSDoc etiketlerinin kullanımını gösterir.

```javascript
/** @description Determines the area of a circle that has the specified radius parameter.
 * @param {number} radius The radius of the circle.
 * @return {number}
 */
function getArea(radius) {
    var areaVal;
    areaVal = Math.PI * radius * radius;
    return areaVal;
}
```

 Yukarıdaki örnekte, IntelliSense `getArea` için açma ayracı yazdığınızda açıklama, parametre ve dönüş bilgilerini gösterir.

 ![Bir işlev için IntelliSense bilgileri](../ide/media/js-intellisense-jsdoc-comments.png "JS_IntelliSense_JSDoc_Comments")

 Aşağıdaki örnek, @typedef etiketinin @property etiketiyle nasıl kullanılacağını gösterir.

```javascript
/**
  * @typedef {object} Weather
  * @property {string} current The current weather.
  */
function getForecast(Weather) {
}

var w = new Weather();
```

 Aşağıdaki örnek @type JSDoc etiketlerinin kullanımını gösterir. Bu örnekte gösterildiği gibi, başlangıçtaki yıldız çiftini (\* \*) izleyen tek yıldız işareti (*) gerekli değildir.

```javascript
/**
    @type {string}
*/
const RED = 'FF0000';

```

 Aşağıdaki örnek, @deprecated JSDoc etiketinin nasıl kullanılacağını göstermektedir.

```javascript
/**
 * @deprecated since version 2.0
 */
function old() {
}
```
