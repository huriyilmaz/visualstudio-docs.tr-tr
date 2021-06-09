---
title: JavaScript ve TypeScript
description: Mac için Visual Studio'de JavaScript desteği hakkında Mac için Visual Studio
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/03/2018
ms.technology: vs-ide-general
ms.assetid: 61432695-5B12-4257-B250-48D37EED106D
ms.openlocfilehash: 5f1a400506f7766ba22ffbc1debde687b1709a21
ms.sourcegitcommit: 01a411cd7ae3488b7b979a947bca92fd296a98e9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2021
ms.locfileid: "111760932"
---
# <a name="javascript-and-typescript-support"></a>JavaScript ve TypeScript desteği

Mac için Visual Studio, söz dizimi vurgulama, kod biçimlendirme ve IntelliSense aracılığıyla JavaScript ve TypeScript için destek sağlar.

![typescript düzenleyicisi desteği](/visualstudio/mac/media/tsjseditor-2019.gif)

JavaScript yazma hakkında daha fazla bilgi için bkz. [JavaScript Kodu](/scripting/javascript/writing-javascript-code) Yazma kılavuzları.

## <a name="adding-a-javascript-file"></a>JavaScript dosyası ekleme

JavaScript dosyaları genellikle Yeni Dosya ASP.NET Core **projelerine** eklenir. Javascript dosyası eklemek için projenize sağ tıklayın ve Yeni Dosya **ekle'> gidin:**

![projeye yeni dosyalar ekleme](media/javascript-image1.png)

Yeni Dosya **iletişim kutusunda Web** Uygulaması Boş **JS >** Veya Web uygulaması **TypeScript > seçin.** Bir ad girin ve Yeni'yi **seçin:**

![şablondan yeni bir typescript dosyası oluşturma](media/javascript-image2.png)

## <a name="intellisense"></a>IntelliSense

Mac için Visual Studio, [IntelliSense JavaScript Language Service,](/visualstudio/ide/javascript-intellisense) kod yazarken akıllı kod tamamlama, parametre bilgileri ve üye listelerine sahip olmak için JavaScript Language Service'yi kullanır.

Mac için Visual Studio JavaScript intellisense tür çıkarılması, JSDoc veya TypeScript bildirimine dayalı olabilir.

- **Tür çıkarı–** Bir nesnenin türü, çevreleyen kod bağlamı tarafından an ifade eder. Daha fazla bilgi için Visual Studio [IntelliSense'te tür çıkarı temel alan bölümüne bakın.](/visualstudio/ide/javascript-intellisense#intellisense-based-on-type-inference)
- **JSDoc–** Tür çıkarca doğru tür bilgilerini sağlamayan zamanlar vardır. Bu durumlarda tür bilgileri [JSDoc](https://jsdoc.app/about-getting-started.html) ek açıklamaları tarafından açıkça sağlanmalıdır. Daha fazla bilgi için Visual Studio [IntelliSense'in JSDoc'yi temel alan bölümüne bakın](/visualstudio/ide/javascript-intellisense#intellisense-based-on-jsdoc)
- **TypeScript bildirim dosyaları** – `.d.ts` Dosyalar JavaScript IntelliSense için değer sağlamak için kullanılır. Bu dosyada bildirilen türler JSDoc açıklamalarında tür olarak kullanılabilir. Daha fazla bilgi için Visual Studio [IntelliSense'in TypeScript](/visualstudio/ide/javascript-intellisense#intellisense-based-on-typescript-declaration-files) bildirim dosyalarını temel alan bölümüne bakın

    ![typescript tanım dosyası ekleme](media/javascript-image3.png)

## <a name="see-also"></a>Ayrıca bkz.

- [JavaScript IntelliSense (Visual Studio Windows üzerinde)](/visualstudio/ide/javascript-intellisense)
