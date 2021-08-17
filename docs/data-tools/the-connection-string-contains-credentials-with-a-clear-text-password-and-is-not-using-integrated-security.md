---
title: Bağlantı dizesi parola içeriyor
description: Bağlantı dizesi şifresiz parola içeren kimlik bilgileri içeriyor ve tümleşik güvenliği kullanmıyor
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 501d85af-92e0-4471-b280-8a59c0688575
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 8e7e5d2eca2506ef0d4e3de3968ffc85b01c6dd5b5508a620435d3ac2b069821
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121346823"
---
# <a name="the-connection-string-contains-credentials-with-a-clear-text-password-and-is-not-using-integrated-security"></a>Bağlantı dizesi şifresiz parola içeren kimlik bilgileri içeriyor ve tümleşik güvenliği kullanmıyor

Bağlantı dizesini bu hassas bilgilerle geçerli DBML dosyasına ve uygulama yapılandırma dosyalarına kaydetmek istiyor musunuz?  Bağlantı **dizesini** hassas bilgiler olmadan kaydetmek için Hayır'a tıklayın.

Hassas bilgiler (bağlantı dizesine dahil olan parolalar) içeren veri bağlantılarıyla çalışırken, bağlantı dizesini projenin DBML dosyasına ve uygulama yapılandırma dosyasına hassas bilgilerle veya hassas bilgiler olmadan kaydetme seçeneği verilir.

> [!WARNING]
> Application Ayarlar  Bağlantı **özellikleri** **özelliğinin False** olarak ayarnması parolayı DBML dosyasına ekler.

## <a name="save-options"></a>Kayıt seçenekleri

- Bağlantı dizesini hassas bilgilerle kaydetmek için Evet'i **seçin.**

   Bağlantı dizesi bir uygulama ayarı olarak depolanır. Bağlantı dizesi, hassas bilgileri düz metin olarak içerir. DBML dosyası hassas bilgileri içermez.

- Bağlantı dizesini hassas bilgiler olmadan kaydetmek için Hayır'ı **seçin.**

   Bağlantı dizesi bir uygulama ayarı olarak depolanır, ancak parola dahil değildir.

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to SQL araçları Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
