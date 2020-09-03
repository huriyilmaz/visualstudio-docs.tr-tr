---
title: Bağlantı dizesi şifresiz parola içeren kimlik bilgileri içeriyor ve tümleşik güvenliği kullanmıyor
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 501d85af-92e0-4471-b280-8a59c0688575
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 201d01d5891b1d788245b2ce61b09f43a50731b1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85281480"
---
# <a name="the-connection-string-contains-credentials-with-a-clear-text-password-and-is-not-using-integrated-security"></a>Bağlantı dizesi şifresiz parola içeren kimlik bilgileri içeriyor ve tümleşik güvenliği kullanmıyor

Bağlantı dizesini geçerli DBML dosyasına ve uygulama yapılandırma dosyalarına bu hassas bilgilerle kaydetmek istiyor musunuz?  Bağlantı dizesini hassas bilgiler olmadan kaydetmek için **Hayır** ' a tıklayın.

Gizli bilgiler (bağlantı dizesinde bulunan parolalar) içeren veri bağlantılarıyla çalışırken, bağlantı dizesini bir projenin DBML dosyasına ve uygulama yapılandırma dosyasına, hassas bilgileri içeren veya olmayan bir şekilde kaydetme seçeneği verilir.

> [!WARNING]
> **Bağlantı** özellikleri **uygulama ayarları** özelliğinin **false** olarak ayarlanması, parolayı dbml dosyasına ekleyecek.

## <a name="save-options"></a>Kayıt seçenekleri

- Bağlantı dizesini hassas bilgilerle kaydetmek için **Evet**' i seçin.

   Bağlantı dizesi bir uygulama ayarı olarak depolanır. Bağlantı dizesi, gizli bilgileri düz metin olarak içerir. DBML dosyası gizli bilgileri içermez.

- Bağlantı dizesini hassas bilgiler olmadan kaydetmek için **Hayır**' ı seçin.

   Bağlantı dizesi bir uygulama ayarı olarak depolanır, ancak parola dahil edilmez.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'da LINQ to SQL araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
