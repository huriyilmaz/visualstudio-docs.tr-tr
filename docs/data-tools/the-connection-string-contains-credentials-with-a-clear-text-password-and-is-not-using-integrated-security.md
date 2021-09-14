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
ms.openlocfilehash: f0394b000239889b9e6444cdf07988f3aaa9d702
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631167"
---
# <a name="the-connection-string-contains-credentials-with-a-clear-text-password-and-is-not-using-integrated-security"></a>Bağlantı dizesi şifresiz parola içeren kimlik bilgileri içeriyor ve tümleşik güvenliği kullanmıyor

Bağlantı dizesini bu hassas bilgilerle geçerli DBML dosyasına ve uygulama yapılandırma dosyalarına kaydetmek istiyor musunuz?  Bağlantı **dizesini** hassas bilgiler olmadan kaydetmek için Hayır'a tıklayın.

Hassas bilgiler (bağlantı dizesine dahil olan parolalar) içeren veri bağlantılarıyla çalışırken, bağlantı dizesini projenin DBML dosyasına ve hassas bilgilerle veya hassas bilgiler olmadan uygulama yapılandırma dosyasına kaydetme seçeneği verilir.

> [!WARNING]
> Application Ayarlar  Bağlantı **özellikleri** **özelliğinin False** olarak açıkça ayarı, parolayı DBML dosyasına ekler.

## <a name="save-options"></a>Kayıt seçenekleri

- Bağlantı dizesini hassas bilgilerle kaydetmek için Evet'i **seçin.**

   Bağlantı dizesi bir uygulama ayarı olarak depolanır. Bağlantı dizesi, hassas bilgileri düz metin olarak içerir. DBML dosyası hassas bilgileri içermez.

- Bağlantı dizesini hassas bilgiler olmadan kaydetmek için Hayır'ı **seçin.**

   Bağlantı dizesi bir uygulama ayarı olarak depolanır, ancak parola dahil değildir.

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to SQL araçları Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
