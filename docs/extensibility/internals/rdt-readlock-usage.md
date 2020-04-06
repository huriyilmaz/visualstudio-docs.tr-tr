---
title: RDT_ReadLock Kullanımı | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- RDT_ReadLock
- visible
- RDT_EditLock
- invisible
ms.assetid: b935fc82-9d6b-4a8d-9b70-e9a5c5ad4a55
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fb897fab61e1e14b52863b5853748c685200d5ba
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705924"
---
# <a name="rdt_readlock-usage"></a>RDT_ReadLock Kullanımı

[_VSRDTFLAGS. RDT_ReadLock,](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_ReadLock>) Visual Studio IDE'de şu anda açık olan tüm belgelerin listesi olan Çalışan Belge Tablosu'nda (RDT) belgeyi kilitlememantığı sağlayan bir bayraktır. Bu bayrak, belgelerin ne zaman açıldığını ve bir belgenin kullanıcı arabiriminde görünür olup olmadığını veya bellekte görünmez bir şekilde tutulup tutulmayacağını belirler.

Genellikle, _VSRDTFLAGS [kullanın. RDT_ReadLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_ReadLock>) aşağıdakilerden biri doğru olduğunda:

- Bir belgeyi görünmez ve salt okunur bir şekilde açmak istiyorsunuz, ancak <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> belgenin sahibi olması gereken henüz belirlenmedi.

- Kullanıcı, kullanıcı kullanıcı kullanıcı tarafından görüntülenmeden önce görünmez bir şekilde açılmış bir belgeyi kaydetmesi ve ardından kapatmayı denemesi için kullanıcıdan istenmesini istiyorsunuz.

## <a name="how-to-manage-visible-and-invisible-documents"></a>Görünür ve Görünmez Belgeler Nasıl Yönetilir?

Kullanıcı Kullanıcı Arabirimi'nde bir belge <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> açtığında, belgenin sahibi oluşturulmalı ve [_VSRDTFLAGS. RDT_EditLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_EditLock>) bayrak ayarlanmalıdır. <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Sahip oluşturulamıyorsa, kullanıcı **Tümlerini Kaydet'i** tıklattığında veya IDE'yi kapattığında belge kaydedilmez. Bu, bir belgenin bellekte değiştirildiği yerde görünmez bir şekilde açık olduğu ve kullanıcıdan belgeyi kapatmaya kaydetmesi `RDT_ReadLock` istenirse veya **Tümlerini Kaydet** seçilirse kaydedilirse, bir belge kullanılamaz. Bunun yerine, bir `RDT_EditLock` __VSREGDOCLOCKHOLDER <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> kullanmak ve bir zaman kayıt [gerekir. RDLH_WeakLockHolder](<xref:Microsoft.VisualStudio.Shell.Interop.__VSREGDOCLOCKHOLDER.RDLH_WeakLockHolder>) bayrak.

## <a name="rdt_editlock-and-document-modification"></a>RDT_EditLock ve Belge Değişikliği

Belirtilen önceki bayrak, belgenin kullanıcı tarafından görünür `RDT_EditLock` bir DocumentWindow'a açıldığında belgenin görünmez açılımının görünür bir **DocumentWindow'a**veriş olacağını gösterir. Bu durumda, görünür **DocumentWindow** kapatıldığında kullanıcıya bir **Kaydet** istemi sunulur. `Microsoft.VisualStudio.Package.Automation.OAProject.CodeModel`<xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager> hizmeti kullanan uygulamalar başlangıçta yalnızca bir `RDT_ReadLock` alındığında (örn. belge görünmez bir şekilde bilgileri ayrıştırmak için açıldığında) çalışır. Daha sonra, belgenin değiştirilmesi gerekiyorsa, kilit zayıf bir **RDT_EditLock**yükseltilir. Kullanıcı daha sonra belgeyi görünür bir **DocumentWindow'da**açarsa, `CodeModel`'zayıf' `RDT_EditLock` serbest bırakılır.

Kullanıcı daha sonra **DocumentWindow'u** kapatır ve açık belgeyi kaydetmek istendiğinde `CodeModel` **Hayır'ı** seçerse, uygulama belgedeki tüm bilgileri elden kaldırır ve belge için bir dahaki sefere daha fazla bilgi gerektiğinde belgeyi görünmez bir şekilde diskten yeniden açar. Bu davranışın inceliği, kullanıcının görünmez açık belgenin **DocumentWindow'u** açtığı, onu modibele ettiği, kapattığı ve belgeyi kaydetmek istendiğinde **Hayır'ı** seçtiği bir örnektir. Bu durumda, belgenin bir `RDT_ReadLock`, sonra belge aslında kapalı değildir ve kullanıcı belgeyi kaydetmek için seçti rağmen değiştirilmiş belge görünmez bellekte açık kalır.

Belgenin görünmez açıklığı zayıf `RDT_EditLock`kullanırsa, kullanıcı belgeyi görünür bir şekilde açtığında ve başka kilit tutulmadığında kilidi verir. Kullanıcı **DocumentWindow'u** kapatıp belgeyi kaydetmek istendiğinde **Hayır'ı** seçtiğinde, belgenin bellekten kapatılması gerekir. Bu, görünmez istemcinin bu oluşumu izlemek için RDT olaylarını dinlemesi gerektiği anlamına gelir. Belgenin bir sonraki gerekliolduğunda, belgenin yeniden açılması gerekir.
