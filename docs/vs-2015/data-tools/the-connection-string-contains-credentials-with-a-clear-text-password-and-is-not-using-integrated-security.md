---
title: Bağlantı dizesi, şifresiz bir metin parolasıyla kimlik bilgileri içeriyor ve tümleşik güvenlik kullanmıyor | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 501d85af-92e0-4471-b280-8a59c0688575
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a8fc2a428753e9650bb0dfebdb2bfdfdde10697a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672282"
---
# <a name="the-connection-string-contains-credentials-with-a-clear-text-password-and-is-not-using-integrated-security"></a>Bağlantı dizesi şifresiz parola içeren kimlik bilgileri içeriyor ve tümleşik güvenliği kullanmıyor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bağlantı dizesini geçerli DBML dosyasına ve uygulama yapılandırma dosyalarına bu hassas bilgilerle kaydetmek istiyor musunuz?  Bağlantı dizesini hassas bilgiler olmadan kaydetmek için Hayır ' a tıklayın.

 Gizli bilgiler (bağlantı dizesinde bulunan parolalar) içeren veri bağlantılarıyla çalışırken, bağlantı dizesini bir projenin DBML dosyasına ve uygulama yapılandırma dosyasına şu şekilde kaydetme seçeneği sunulur hassas bilgiler.

> [!WARNING]
> **Bağlantı** özellikleri **uygulama ayarları** özelliğinin **false** olarak ayarlanması, parolayı dbml dosyasına ekleyecek.

### <a name="to-save-the-connection-string-with-the-sensitive-information-in-the-projects-application-settings"></a>Bağlantı dizesini projenin uygulama ayarlarındaki hassas bilgilerle kaydetmek için

- **Evet**'i tıklayın.

     Bağlantı dizesi bir uygulama ayarı olarak depolanır. Bağlantı dizesi, gizli bilgileri düz metin olarak içerir. DBML dosyası gizli bilgileri içermez.

### <a name="to-save-the-connection-string-without-the-sensitive-information-in-the-projects-application-settings"></a>Bağlantı dizesini projenin uygulama ayarlarındaki gizli bilgiler olmadan kaydetmek için

- **Hayır**'a tıklayın.

     Bağlantı dizesi bir uygulama ayarı olarak depolanır, ancak parola dahil edilmez.

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio'daki LINQ to SQL Araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
