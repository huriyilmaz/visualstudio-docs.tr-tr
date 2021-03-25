---
title: Proje öğelerini açma ve kaydetme | Microsoft Docs
description: Visual Studio IDE 'de yeni proje türü için dosyaları açmak ve kaydetmek üzere farklı yaklaşımlar hakkında bilgi edinin.
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
ms.workload:
- vssdk
ms.openlocfilehash: 6ff3c76294ce99fa5eeb7bf311307e54f5d0e6cc
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105063077"
---
# <a name="opening-and-saving-project-items"></a>Proje Öğelerini Açma ve Kaydetme
Yeni bir proje türü eklediğinizde, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Tümleşik geliştirme ortamında (IDE) proje dosyalarınızın açılmasını ve kaydedilmesini yönetmeniz gerekir. Aşağıdaki konularda, dosyaları açma ve kaydetme ile ilgili farklı yaklaşımlar ele alınmaktadır.

## <a name="in-this-section"></a>Bu Bölümde
- [Dosya Aç Komutunu Kullanarak Dosyaları Görüntüleme](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)

 IDE 'nin **Açık dosya** komutunu ve bu komuta yanıt veren projelerin rolünü nasıl işleydiğinin adım adım açıklaması sağlar.

- [Birlikte Aç Komutunu Kullanarak Dosyaları Görüntüleme](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)

 IDE 'nin, bazı standart düzenleyiciler içeren bir dosyanın açılmasını isteyerek, birlikte Aç komutunu nasıl **Işleyeceğiyle** ilgili ayrıntılı, adım adım bir açıklama sağlar.

- [Nasıl Yapılır: Projeye Özgü Düzenleyicileri Açma](../../extensibility/how-to-open-project-specific-editors.md)

 Projenizdeki belirli bir türdeki dosyaların projeye özgü bir düzenleyici kullanılarak açılması gerektiğini belirtmek için adım adım yönergeler sağlar.

- [Nasıl Yapılır: Standart Düzenleyicileri Açma](../../extensibility/how-to-open-standard-editors.md)

 IDE 'nin proje türündeki dosyalar için standart bir düzenleyici açmasını belirtmeye yönelik adım adım yönergeler sağlar.

- [Nasıl Yapılır: Açık Belgeler için Düzenleyicileri Açma](../../extensibility/how-to-open-editors-for-open-documents.md)

 Açık dosya için projeye özgü bir düzenleyici açmak için adım adım yönergeler sağlar.

- [Standart Belge Kaydetme](../../extensibility/internals/saving-a-standard-document.md)

 IDE 'nin **Kaydet**, **farklı kaydet** ve standart düzenleyicide açılan bir belge için **tüm komutları kaydet** hakkında ayrıntılı bir açıklama sağlar.

- [Özel Belge Kaydetme](../../extensibility/internals/saving-a-custom-document.md)

 Bir diyagram ve IDE 'nin **Kaydet**, **farklı kaydet** ve özel bir düzenleyicide açılan belgeler için tüm komutları **Kaydet** hakkında ayrıntılı açıklamalar sağlar.

- [Projedeki Bir Dosyayı Hangi Düzenleyicinin Açacağını Belirleme](../../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)

 Bir dosya için uygun düzenleyiciyi veya tasarımcıyı seçmek üzere IDE 'nin izlediği süreci açıklar.

## <a name="related-sections"></a>İlgili Bölümler
- [Özel Düzenleyiciler ve Tasarımcılar Oluşturma](../../extensibility/creating-custom-editors-and-designers.md)

 IDE 'nin barındıra, her düzenleyicinin açıklamalarını verdiği dört düzenleyici türünü listeler.

- [Proje Türleri](../../extensibility/internals/project-types.md)

 Projelerin kodun nasıl derlendiğini, oluşturulduğunu, düzenleyicilerin nasıl açıldığını ve proje öğelerinin nasıl biçimlendirildiğini açıklar.
