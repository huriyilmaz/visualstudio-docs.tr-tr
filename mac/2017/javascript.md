---
title: JavaScript ve TypeScript
description: Mac için Visual Studio JavaScript desteği hakkında bilgi
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/03/2018
ms.technology: vs-ide-general
ms.assetid: 61432695-5B12-4257-B250-48D37EED106D
ms.openlocfilehash: cc10cd6125dc19571424358fd1ce9de46f7d86c5
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "74984907"
---
# <a name="javascript-and-typescript-support"></a>JavaScript ve TypeScript desteği

Mac için Visual Studio sözdizimi vurgulama, kod biçimlendirme ve IntelliSense aracılığıyla JavaScript ve TypeScript için destek sağlar.

![typescript düzenleyici desteği](https://msdnshared.blob.core.windows.net/media/2018/03/TypeScript-editor.gif)

JavaScript yazma hakkında daha fazla bilgi için, [Yazma JavaScript Kodu](/scripting/javascript/writing-javascript-code) kılavuzlarına bakın.

## <a name="adding-a-javascript-file"></a>JavaScript dosyası ekleme

JavaScript dosyaları en sık **Yeni Dosya** iletişim kutusu aracılığıyla ASP.NET Core projelerine eklenir. Javascript dosyası eklemek için projenize sağ tıklayın ve **Yeni Dosya ekle**> gidin:

![projeye yeni dosyalar ekleme](media/javascript-image1.png)

Yeni **Dosya** iletişim kutusundan, Boş JS dosyası veya **Web > TypeScript dosyası**> Web **>'u** seçin. Bir ad verin ve sonra **Yeni**seçin:

![şablondan yeni bir typescript dosyası oluşturma](media/javascript-image2.png)

## <a name="intellisense"></a>IntelliSense

Mac için Visual Studio, IntelliSense sağlamak için [JavaScript Dil Hizmeti'ni](/visualstudio/ide/javascript-intellisense) kullanır ve kod yazarken akıllı kod tamamlama, parametre bilgileri ve üye listelerine sahip olabilirsiniz.

Mac için Visual Studio JavaScript intellisense türü çıkarım, JSDoc veya TypeScript bildirimi dayalı olabilir.

- **Tür çıkarım** - Bir nesnenin türü çevreleyen kod bağlamında çözülr. Daha fazla bilgi için, tür çıkarımlarına göre Visual Studio'nun [IntelliSense'deki bölümüne](/visualstudio/ide/javascript-intellisense#intellisense-based-on-type-inference)bakın.
- **JSDoc** – Tür çıkarımlarının doğru tür bilgilerini sağlamadığı zamanlar vardır. Bu gibi durumlarda, tür bilgileri Açıkça [JSDoc](https://jsdoc.app/about-getting-started.html) ek açıklamalar tarafından sağlanabilir. Daha fazla bilgi için Visual Studio'nun [JSDoc'a dayalı IntelliSense bölümüne](/visualstudio/ide/javascript-intellisense#intellisense-based-on-jsdoc) bakın
- **TypeScript bildirim** `.d.ts` dosyaları – dosyalar JavaScript IntelliSense için değerler sağlamak için kullanılır. Bu dosyada bildirilen türler JSDoc yorumlarında tür olarak kullanılabilir. Daha fazla bilgi için, TypeScript bildirim dosyalarına dayalı Olarak Visual Studio'nun [IntelliSense bölümüne](/visualstudio/ide/javascript-intellisense#intellisense-based-on-typescript-declaration-files) bakın

    ![typescript tanım dosyası ekleme](media/javascript-image3.png)

## <a name="see-also"></a>Ayrıca bkz.

- [JavaScript IntelliSense (Windows'da Visual Studio)](/visualstudio/ide/javascript-intellisense)
