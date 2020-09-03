---
title: JavaScript ve TypeScript
description: Mac için Visual Studio JavaScript desteği hakkında bilgi
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/03/2018
ms.technology: vs-ide-general
ms.assetid: 61432695-5B12-4257-B250-48D37EED106D
ms.openlocfilehash: cc10cd6125dc19571424358fd1ce9de46f7d86c5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74984907"
---
# <a name="javascript-and-typescript-support"></a>JavaScript ve TypeScript desteği

Mac için Visual Studio, sözdizimi vurgulama, kod biçimlendirme ve IntelliSense aracılığıyla JavaScript ve TypeScript desteği sağlar.

![TypeScript Düzenleyicisi desteği](https://msdnshared.blob.core.windows.net/media/2018/03/TypeScript-editor.gif)

JavaScript yazma hakkında daha fazla bilgi için bkz. [JavaScript kod kılavuzlarını yazma](/scripting/javascript/writing-javascript-code) .

## <a name="adding-a-javascript-file"></a>JavaScript dosyası ekleme

JavaScript dosyaları en sık **yeni dosya** iletişim kutusu üzerinden ASP.NET Core projelerine eklenir. Bir JavaScript dosyası eklemek için projenize sağ tıklayın ve **> yeni dosya Ekle**' ye gidin:

![projeye yeni dosyalar ekleniyor](media/javascript-image1.png)

**Yeni dosya** Iletişim kutusundan **Web > boş js dosyası** veya **Web > TypeScript dosyası**' nı seçin. Bir ad verin ve ardından **Yeni**' yi seçin:

![şablondan yeni bir TypeScript dosyası oluşturma](media/javascript-image2.png)

## <a name="intellisense"></a>IntelliSense

Mac için Visual Studio, IntelliSense sağlamak için [JavaScript Language Service](/visualstudio/ide/javascript-intellisense) kullanır, böylece kod yazarken akıllı kod tamamlama, parametre bilgisi ve üye listelerinin olması sağlanır.

Mac için Visual Studio içindeki JavaScript IntelliSense, tür çıkarımı, JSDoc veya TypeScript bildirimine göre yapılabilir.

- **Tür çıkarımı** : bir nesnenin türü, çevreleyen kod bağlamı tarafından iletişime. Daha fazla bilgi için bkz. [tür çıkarımı temelinde IntelliSense](/visualstudio/ide/javascript-intellisense#intellisense-based-on-type-inference)üzerinde Visual Studio bölümü.
- **JSDoc** : tür çıkarımı doğru tür bilgilerini sağlamıyorsa zaman vardır. Bu gibi durumlarda, tür bilgileri açıkça [JSDoc](https://jsdoc.app/about-getting-started.html) ek açıklamaları tarafından sağlanmış olabilir. Daha fazla bilgi için bkz. Visual Studio 'nun [IntelliSense 'de JSDoc tabanlı](/visualstudio/ide/javascript-intellisense#intellisense-based-on-jsdoc) bölümü
- **TypeScript bildirim dosyaları** – `.d.ts` dosyalar, JavaScript IntelliSense için değerler sağlamak üzere kullanılır. Bu dosyada bildirildiği türler, JSDoc açıklamalarında türler olarak kullanılabilir. Daha fazla bilgi için bkz. [TypeScript bildirim dosyalarını temel alan IntelliSense](/visualstudio/ide/javascript-intellisense#intellisense-based-on-typescript-declaration-files) üzerinde Visual Studio 'nun bölümü

    ![TypeScript tanım dosyası ekleniyor](media/javascript-image3.png)

## <a name="see-also"></a>Ayrıca bkz.

- [JavaScript IntelliSense (Windows üzerinde Visual Studio)](/visualstudio/ide/javascript-intellisense)
