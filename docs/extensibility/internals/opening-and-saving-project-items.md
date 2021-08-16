---
title: Öğeleri Açma Project Kaydetme | Microsoft Docs
description: IDE'de yeni proje türünüz için dosyaları açma ve kaydetmeye yönelik farklı Visual Studio öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], file persistence
- files [Visual Studio], opening and saving
- editors [Visual Studio SDK], file persistence
ms.assetid: f71898ad-335f-4c43-a177-4da87078afd1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 7cdf47d983d7070c0cc1a407a5a32f6e661b36cb85ef0310d06be112c2cb0816
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121359305"
---
# <a name="opening-and-saving-project-items"></a>Proje Öğelerini Açma ve Kaydetme
Yeni bir proje türü eklerken, proje dosyalarınızın tümleşik geliştirme ortamında [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (IDE) açılmasını ve kaydedisini yönetmeniz gerekir. Aşağıdaki konular, dosyaları açma ve kaydetmeye yönelik farklı yaklaşımları ele almaktadır.

## <a name="in-this-section"></a>Bu Bölümde
- [Dosya Aç Komutunu Kullanarak Dosyaları Görüntüleme](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)

 IDE'nin Dosya Aç komutunu nasıl işleyene ve bu komuta yanıt veren projelerin rolüne ilişkin adım adım bir açıklama sağlar. 

- [Birlikte Aç Komutunu Kullanarak Dosyaları Görüntüleme](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)

 IDE'nin Birlikte Aç komutunu nasıl işlediğinde ayrıntılı, adım adım bir açıklama sağlar ve bazı standart düzenleyiciler seçeneğine sahip bir dosyanın açılmasını ister. 

- [Nasıl Yapılır: Projeye Özgü Düzenleyicileri Açma](../../extensibility/how-to-open-project-specific-editors.md)

 Projenizin belirli bir türüne sahip dosyaların projeye özgü bir düzenleyici kullanılarak açılması gerektiğini belirtmek için adım adım yönergeler sağlar.

- [Nasıl Yapılır: Standart Düzenleyicileri Açma](../../extensibility/how-to-open-standard-editors.md)

 IDE'nin proje türünüzde dosyalar için standart bir düzenleyiciyi açması için etkinleştirmeyi belirtmek için adım adım yönergeler sağlar.

- [Nasıl Yapılır: Açık Belgeler için Düzenleyicileri Açma](../../extensibility/how-to-open-editors-for-open-documents.md)

 Açık bir dosya için projeye özgü bir düzenleyiciyi açmak için adım adım yönergeler sağlar.

- [Standart Belge Kaydetme](../../extensibility/internals/saving-a-standard-document.md)

 IDE'nin standart bir düzenleyicide açılan bir belge  için **Kaydet,** **Farklı** Kaydet ve Tüm Komutları Kaydet komutlarını nasıl işleye dair ayrıntılı bir açıklama sağlar.

- [Özel Belge Kaydetme](../../extensibility/internals/saving-a-custom-document.md)

 IDE'nin özel bir düzenleyicide açılan belgeler için **Kaydet,** Farklı Kaydet ve Tüm Komutları Kaydet komutlarını nasıl işleye dair ayrıntılı bir açıklama ve diyagram sağlar. 

- [Projedeki Bir Dosyayı Hangi Düzenleyicinin Açacağını Belirleme](../../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)

 IDE'nin bir dosya için uygun düzenleyiciyi veya tasarımcıyı seçme işlemini ele almaktadır.

## <a name="related-sections"></a>İlgili Bölümler
- [Özel Düzenleyiciler ve Tasarımcılar Oluşturma](../../extensibility/creating-custom-editors-and-designers.md)

 IDE'nin barındırabilirsiniz dört düzenleyici türü listeler ve her düzenleyicinin açıklamalarını verir.

- [Proje Türleri](../../extensibility/internals/project-types.md)

 Projelerin kodun derlenmiş ve derlenmiş bir şekilde nasıl kontrol altında olduğunu, düzenleyicilerin nasıl açılamadılarını ve proje öğelerinin nasıl biçimlendirildiklerini ele almaktadır.
