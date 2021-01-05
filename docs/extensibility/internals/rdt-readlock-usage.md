---
title: RDT_ReadLock kullanımı | Microsoft Docs
description: _VSRDTFLAGS hakkında bilgi edinin. Çalışan belge tablosunda bir belgeyi kilitlemek için mantık sağlayan RDT_ReadLock bayrak.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 2c946d69cf1aded072d27e7c6ccbdf28f1122571
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97875394"
---
# <a name="rdt_readlock-usage"></a>RDT_ReadLock Kullanımı

[_VSRDTFLAGS. RDT_ReadLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_ReadLock>) , Visual STUDIO IDE 'de Şu anda açık olan tüm belgelerin listesi olan çalışan belge tablosunda (RDT) bir belgeyi kilitlemek için mantık sağlayan bir bayrak. Bu bayrak belgelerin ne zaman açılacağını ve bir belgenin Kullanıcı arabiriminde görünüp görünmeyeceğini ya da bellekte görünmediğini belirler.

Genellikle [_VSRDTFLAGS kullanırsınız. ](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_ReadLock>) Aşağıdakilerden biri doğru olduğunda RDT_ReadLock:

- Bir belgeyi görünür ve salt okunurdur, ancak henüz kendisine ait olması gereken bir belge yok <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> .

- Kullanıcıdan Kullanıcı ARABIRIMINDE görüntülenmeden önce açık bir şekilde açılan bir belgeyi kaydetmesi istenir ve sonra kapatmayı denemelidir.

## <a name="how-to-manage-visible-and-invisible-documents"></a>Görünür ve görünmeyen belgeleri yönetme

Kullanıcı Kullanıcı ARABIRIMINDE bir belge açtığında, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Belgenin sahibi oluşturulmalıdır ve bir [_VSRDTFLAGS. RDT_EditLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_EditLock>) bayrağının ayarlanması gerekir. Sahip yoksa <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> , Kullanıcı **Tümünü Kaydet** ' e tıkladığında veya IDE 'yi kapattığında belge kaydedilmez. Bu, bir belgenin bellekte değiştirildiği yerde açık bir şekilde açıksa ve **Tümünü Kaydet** seçilirse kullanıcının belgeyi kapanmaya kaydetmesi veya kaydedilmesi istenirse, `RDT_ReadLock` kullanılamaz hale gelir. Bunun yerine, bir __VSREGDOCLOCKHOLDER kullandığınızda `RDT_EditLock` bir ve kaydetmeniz gerekir <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> [. RDLH_WeakLockHolder](<xref:Microsoft.VisualStudio.Shell.Interop.__VSREGDOCLOCKHOLDER.RDLH_WeakLockHolder>) bayrak.

## <a name="rdt_editlock-and-document-modification"></a>RDT_EditLock ve belge değiştirme

Bahsedilen önceki bayrak, belge `RDT_EditLock` Kullanıcı tarafından görünür bir **DocumentWindow**'a açıldığında belgenin görünmez bir şekilde açılması gerektiğini gösterir. Bu gerçekleştiğinde, görünür **DocumentWindow** kapalıyken kullanıcıya bir **kaydetme** istemi sunulur. `Microsoft.VisualStudio.Package.Automation.OAProject.CodeModel` hizmeti ilk olarak kullanan uygulamalar, <xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager> yalnızca bir alındığı zaman `RDT_ReadLock` (yani, belge bilgileri ayrıştırılmaya açık bir şekilde açıldığında) çalışır. Daha sonra, belgenin değiştirilmesi gerekiyorsa, kilit zayıf bir **RDT_EditLock** yükseltilir. Kullanıcı belgeyi görünür bir **DocumentWindow**'ta açarsa, `CodeModel` zayıf `RDT_EditLock` olur.

Kullanıcı daha sonra **DocumentWindow** 'u kapatır ve açık belgeyi kaydetmek isteyip **istemediğiniz sorulduğunda,** `CodeModel` uygulama belgedeki tüm bilgileri atar ve belge için daha fazla bilgi gerektiğinde belgeyi diskten yeniden açar. Bu davranışın alt tlonu, kullanıcının görünmeyen açık belgenin **DocumentWindow** 'u açtığı, değiştirdiği, kapattığı ve sonra belgeyi kaydetmesi istendiğinde **Hayır** ' ı seçtiği bir örneğidir. Bu durumda, belgenin bir olması halinde belge `RDT_ReadLock` aslında kapanmaz ve değiştirilen belge, Kullanıcı belgeyi Kaydetmemeyi tercih etmese de, değiştirilen belge, bellekte açık olarak kalır.

Belgenin görünmez bir şekilde açılması zayıf bir kullanırsa `RDT_EditLock` , Kullanıcı belgeyi bir daha açıp başka bir kilit tutulmadığında kilidi verir. Kullanıcı **DocumentWindow** 'u kapattığında ve belgeyi kaydetmek isteyip Istemediğiniz sorulduğunda **Hayır** ' ı seçtiğinde, belgenin bellekten kapatılması gerekir. Bu, görünmeyen istemcinin bu oluşumu izlemek için RDT olaylarını dinlemesi gerektiği anlamına gelir. Belge bir dahaki sefer gerekliyse, belgenin yeniden açılması gerekir.
