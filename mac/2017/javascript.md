---
title: JavaScript ve TypeScript
description: Mac için Visual Studio'de JavaScript desteği hakkında Mac için Visual Studio
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/03/2018
ms.technology: vs-ide-general
ms.assetid: 61432695-5B12-4257-B250-48D37EED106D
ms.openlocfilehash: 2b0a302eabfa2db7830a3da7372153bf9f17ed086020d8fb8fa879cc87cf2edc
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121439820"
---
# <a name="javascript-and-typescript-support"></a>JavaScript ve TypeScript desteği

Mac için Visual Studio, söz dizimi vurgulama, kod biçimlendirme ve IntelliSense aracılığıyla JavaScript ve TypeScript için destek sağlar.

![typescript düzenleyicisi desteği](/visualstudio/mac/media/tsjseditor-2019.gif)

JavaScript yazma hakkında daha fazla bilgi için bkz. [JavaScript Kodu](/scripting/javascript/writing-javascript-code) Yazma kılavuzları.

## <a name="adding-a-javascript-file"></a>JavaScript dosyası ekleme

JavaScript dosyaları genellikle yeni ASP.NET Core iletişim kutusu aracılığıyla yeni **projelere** eklenir. Javascript dosyası eklemek için projenize sağ tıklayın ve Yeni Dosya **Ekle'> gidin:**

![projeye yeni dosyalar ekleme](media/javascript-image1.png)

Yeni Dosya **iletişim kutusunda Web** Uygulaması Boş **JS >** Veya TypeScript dosyası web > **seçin.** Bir ad girin ve Yeni'yi **seçin:**

![şablondan yeni bir typescript dosyası oluşturma](media/javascript-image2.png)

## <a name="intellisense"></a>IntelliSense

Mac için Visual Studio, [intellisense JavaScript Language Service,](/visualstudio/ide/javascript-intellisense) kod yazarken akıllı kod tamamlama, parametre bilgileri ve üye listelerine sahip olmak için JavaScript Language Service'yi kullanır.

Mac için Visual Studio javaScript intellisense tür çıkarılması, JSDoc veya TypeScript bildirimine dayalı olabilir.

- **Tür çıkarı–** Bir nesnenin türü, çevreleyen kod bağlamı tarafından an ifade eder. Daha fazla bilgi için Visual Studio [IntelliSense'te tür çıkarı temel alan bölümüne bakın.](/visualstudio/ide/javascript-intellisense#intellisense-based-on-type-inference)
- **JSDoc–** Tür çıkarca doğru tür bilgilerini sağlamayan zamanlar vardır. Bu durumlarda tür bilgileri [JSDoc](https://jsdoc.app/about-getting-started.html) ek açıklamaları tarafından açıkça sağlanmalıdır. Daha fazla bilgi için Visual Studio [IntelliSense'in JSDoc'yi temel alan bölümüne bakın](/visualstudio/ide/javascript-intellisense#intellisense-based-on-jsdoc)
- **TypeScript bildirim dosyaları** – `.d.ts` Dosyalar JavaScript IntelliSense için değer sağlamak için kullanılır. Bu dosyada bildirilen türler JSDoc açıklamalarında tür olarak kullanılabilir. Daha fazla bilgi için Visual Studio [IntelliSense'in TypeScript](/visualstudio/ide/javascript-intellisense#intellisense-based-on-typescript-declaration-files) bildirim dosyalarını temel alan bölümüne bakın

    ![typescript tanım dosyası ekleme](media/javascript-image3.png)

## <a name="see-also"></a>Ayrıca bkz.

- [JavaScript IntelliSense (Visual Studio üzerinde Windows)](/visualstudio/ide/javascript-intellisense)
