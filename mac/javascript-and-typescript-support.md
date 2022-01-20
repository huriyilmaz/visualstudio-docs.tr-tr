---
title: JavaScript ve TypeScript
description: Mac için Visual Studio JavaScript desteği hakkında bilgi
author: jmatthiesen
ms.author: jomatthi
manager: dominicn
ms.date: 05/03/2018
ms.technology: vs-ide-general
ms.topic: how-to
ms.assetid: 61432695-5B12-4257-B250-48D37EED106D
ms.openlocfilehash: bea3a53913bf9e96a14ad18d80d817a1ffafda2f
ms.sourcegitcommit: 1c0eda2db1b1fff9595ca644503f467bf3e223e0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/20/2022
ms.locfileid: "137095882"
---
# <a name="javascript-and-typescript-support"></a>JavaScript ve TypeScript desteği

Mac için Visual Studio, sözdizimi vurgulama, kod biçimlendirme ve ıntellisense aracılığıyla JavaScript ve TypeScript desteği sağlar.

![TypeScript Düzenleyicisi desteği](media/tsjseditor-2019.gif)

JavaScript yazma hakkında daha fazla bilgi için bkz. [JavaScript kod kılavuzlarını yazma](/scripting/javascript/writing-javascript-code) .

## <a name="adding-a-javascript-file"></a>JavaScript dosyası ekleme

JavaScript dosyaları en sık **yeni dosya** iletişim kutusu üzerinden ASP.NET Core projelerine eklenir. Bir JavaScript dosyası eklemek için projenize sağ tıklayın ve **> yeni dosya Ekle**' ye gidin:

![projeye yeni dosyalar ekleniyor](media/javascript-image1.png)

**Yeni dosya** Iletişim kutusundan **Web > boş js dosyası** veya **Web > TypeScript dosyası**' nı seçin. Bir ad verin ve ardından **Yeni**' yi seçin:

![şablondan yeni bir TypeScript dosyası oluşturma](media/javascript-image2.png)

## <a name="intellisense"></a>IntelliSense

Mac için Visual Studio, ıntellisense sağlamak için [JavaScript Language Service](/visualstudio/ide/javascript-intellisense) kullanır, böylece kod yazarken akıllı kod tamamlama, parametre bilgisi ve üye listelerinin olması sağlanır.

Mac için Visual Studio içindeki JavaScript ıntellisense, tür çıkarımı, jsdoc veya TypeScript bildirimlerini temel alabilir.

- **Tür çıkarımı** : bir nesnenin türü, çevreleyen kod bağlamı tarafından iletişime. daha fazla bilgi için bkz. [tür çıkarımı temelinde ıntellisense](/visualstudio/ide/javascript-intellisense#intellisense-based-on-type-inference)'teki Visual Studio bölümü.
- **JSDoc** : tür çıkarımı doğru tür bilgilerini sağlamıyorsa zaman vardır. Bu gibi durumlarda, tür bilgileri açıkça [JSDoc](https://jsdoc.app/about-getting-started.html) ek açıklamaları tarafından sağlanmış olabilir. daha fazla bilgi için bkz. [jsdoc tabanlı ıntellisense](/visualstudio/ide/javascript-intellisense#intellisense-based-on-jsdoc) 'teki Visual Studio bölümü
- **TypeScript bildirim dosyaları** – `.d.ts` dosyalar, JavaScript IntelliSense için değerler sağlamak üzere kullanılır. Bu dosyada bildirildiği türler, JSDoc açıklamalarında türler olarak kullanılabilir. daha fazla bilgi için bkz. [TypeScript bildirim dosyalarına göre ıntellisense](/visualstudio/ide/javascript-intellisense#intellisense-based-on-typescript-declaration-files) üzerinde Visual Studio bölümü

    ![TypeScript tanım dosyası ekleniyor](media/javascript-type-intellisense-2019.gif)

## <a name="see-also"></a>Ayrıca bkz.

- [JavaScript ıntellisense (Windows Visual Studio)](/visualstudio/ide/javascript-intellisense)
