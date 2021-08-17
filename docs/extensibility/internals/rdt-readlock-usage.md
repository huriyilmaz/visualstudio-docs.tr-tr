---
title: RDT_ReadLock Kullanımı | Microsoft Docs
description: Aşağıdakiler hakkında bilgi _VSRDTFLAGS. RDT_ReadLock bayrağı, Çalışan Belge Tablosu'da bir belgeyi kilitleme mantığı sağlar.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- RDT_ReadLock
- visible
- RDT_EditLock
- invisible
ms.assetid: b935fc82-9d6b-4a8d-9b70-e9a5c5ad4a55
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 4fc969570ac392fdef86782ffb2d9ea9052c91e2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122028862"
---
# <a name="rdt_readlock-usage"></a>RDT_ReadLock Kullanımı

[_VSRDTFLAGS. RDT_ReadLock,](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_ReadLock>) O anda IDE'de açık olan tüm belgelerin listesi olan Çalışan Belge Tablosu'nda (RDT) bir belgeyi kilitleme mantığı sağlayan Visual Studio bayrağıdır. Bu bayrak, belgelerin ne zaman açılamadı gerçekleştirilen ve bir belgenin kullanıcı arabiriminde görünür olup olmadığını veya bellekte görünmeden tutularak belirler.

Genel olarak, [_VSRDTFLAGS. RDT_ReadLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_ReadLock>) doğru olduğunda şunları yapabilirsiniz:

- Bir belgeyi görsel olarak ve salt okunur olarak açmak istiyor ancak henüz belgeye sahip olması gereken belge <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> henüz belirlenmedi.

- Kullanıcıdan, kullanıcı arabiriminde görüntülenmeden ve sonra kapatma girişiminde bulunmadan önce, görünür şekilde açılmış bir belgeyi kaydetmesi istensin.

## <a name="how-to-manage-visible-and-invisible-documents"></a>Görünür ve Görünmez Belgeleri Yönetme

Kullanıcı kullanıcı arabiriminde bir belge açtığında, belgenin sahibi oluşturularak bir belge <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> [_VSRDTFLAGS. RDT_EditLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_EditLock>) bayrağı ayarlandı. Sahip <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> oluşturulamayacaksa, kullanıcı Hepsini Kaydet'e tıkladığında  veya IDE'ye tıkladığında belge kaydedilemiyor. Bu, bir belgenin bellekte değiştirildiğinde görsel olarak açık olduğu ve kullanıcıdan kapatma sırasında belgeyi  kaydetmesi veya Tüm Kaydet seçilirse belgeyi kaydetmesi istendiğinde, bir `RDT_ReadLock` kullanılamaz. Bunun yerine, bir kullanarak bir `RDT_EditLock` kayıt <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> [__VSREGDOCLOCKHOLDER. RDLH_WeakLockHolder](<xref:Microsoft.VisualStudio.Shell.Interop.__VSREGDOCLOCKHOLDER.RDLH_WeakLockHolder>) bayrağı.

## <a name="rdt_editlock-and-document-modification"></a>RDT_EditLock ve Belge Değişikliği

Belirtilen önceki bayrak, belge kullanıcı tarafından görünür bir DocumentWindow olarak açıldığında belgenin görünmez bir şekilde açılmasının belgeyi `RDT_EditLock` ver **olduğunu gösterir.** Bu durum oluştuğunda, görünür **DocumentWindow** **kapatılan** kullanıcıya bir Kaydet istemi görünür. `Microsoft.VisualStudio.Package.Automation.OAProject.CodeModel` hizmetini kullanan uygulamalar başlangıçta yalnızca bir alınarak (örneğin, belge bilgileri ayrıştırmak için görünür olarak <xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager> `RDT_ReadLock` açıldığında) çalışır. Daha sonra, belgenin değiştirilmesi gerekirse, kilit daha sonra zayıf bir sürüme **RDT_EditLock.** Kullanıcı daha sonra belgeyi görünür bir **DocumentWindow** içinde açarsa, `CodeModel` 'ın `RDT_EditLock` zayıfı serbesttir.

Kullanıcı **DocumentWindow'ı** kapatır ve açık  belgeyi kaydetmesi istendiğinde Hayır'ı seçerse, uygulama belgede yer alan tüm bilgileri atarak belge için daha fazla bilgi `CodeModel` gerektiğinde, belgeyi görsel olarak yeniden açar. Bu davranışın inceliği, kullanıcının görünmez açık belgenin **DocumentWindow'larını** açtığı, belgeyi değiştiren, kapatan  ve ardından belgeyi kaydetmesi istendiğinde Hayır'ı seçen bir örnektir. Bu durumda, belgede bir varsa, kullanıcı belgeyi kaydetmeyi seçmese bile belge aslında kapatılacak ve değiştirilen belge bellekte görsel olarak `RDT_ReadLock` açık kalır.

Belgenin görünmez açması zayıf bir kullanırsa, kullanıcı belgeyi görünür bir şekilde açtığında ve başka kilitler tutulmasa `RDT_EditLock` kilitlenir. Kullanıcı **DocumentWindow'ı** kapatıp belgeyi  kaydetmesi istendiğinde Hayır'ı seçerse, belgenin bellekten kapatılmış olması gerekir. Bu, görünmez istemcinin bu oluşumunu izlemek için RDT olaylarını dinlemesi gereken anlamına gelir. Belgeye bir sonraki ihtiyaç için belgenin yeniden açılması gerekir.
