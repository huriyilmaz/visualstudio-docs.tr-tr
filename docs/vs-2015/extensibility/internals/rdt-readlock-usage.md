---
title: RDT_ReadLock kullanımı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- RDT_ReadLock
- visible
- RDT_EditLock
- invisible
ms.assetid: b935fc82-9d6b-4a8d-9b70-e9a5c5ad4a55
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a9a6b5f86f0cfbb71f6264bdc74df72ad9209c9d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68154139"
---
# <a name="rdt_readlock-usage"></a>RDT_ReadLock Kullanımı
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> , Visual Studio IDE 'de açık olan tüm belgelerin listesi olan çalışan belge tablosunda (RDT) bir belgeyi kilitlemek için mantık sağlayan bir bayrak. Bu bayrak belgelerin ne zaman açılacağını ve bir belgenin Kullanıcı arabiriminde görünüp görünmeyeceğini ya da bellekte görünmediğini belirler.  
  
 Genellikle, <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> aşağıdakilerden biri doğru olduğunda öğesini kullanabilirsiniz:  
  
- Bir belgeyi açık ve salt okunurdur bir belge açmak istediğinizde, bu henüz kendisine <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> ait olmalıdır.  
  
- Kullanıcıdan Kullanıcı ARABIRIMINDE görüntülemeden önce açık bir şekilde açılan bir belgeyi kaydetmesi istenir ve ardından bunu kapatmaya çalışınız.  
  
## <a name="how-to-manage-visible-and-invisible-documents"></a>Görünür ve görünmeyen belgeleri yönetme  
 Kullanıcı Kullanıcı ARABIRIMINDE bir belge açtığında, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> belge için bir sahip oluşturulması ve bir <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> bayrağın ayarlanması gerekir. Sahip yoksa <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> , Kullanıcı **Tümünü Kaydet** ' e tıkladığında veya IDE 'yi kapattığında belge kaydedilmez. Bu, bir belgenin bellekte değiştirildiği yerde açık bir şekilde açıksa ve **Tümünü Kaydet** seçilirse kullanıcının belgeyi kapanmaya kaydetmesi veya kaydedilmesi istenirse, `RDT_ReadLock` kullanılamaz hale gelir. Bunun yerine, bir bayrağı kullanmanız `RDT_EditLock` ve bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> bayrak olduğunda kaydetmeniz gerekir <xref:Microsoft.VisualStudio.Shell.Interop.__VSREGDOCLOCKHOLDER> .  
  
## <a name="rdt_editlock-and-document-modification"></a>RDT_EditLock ve belge değiştirme  
 Bahsedilen önceki bayrak, belge `RDT_EditLock` Kullanıcı tarafından görünür bir **DocumentWindow**'a açıldığında belgenin görünmez bir şekilde açılması gerektiğini gösterir. Bu gerçekleştiğinde, görünür **DocumentWindow** kapalıyken kullanıcıya bir **kaydetme** istemi sunulur. Hizmeti kullanan Microsoft. VisualStudio. Package. Automation. OAProject. CodeModel uygulamaları, <xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager> yalnızca bir kez yapıldığında `RDT_ReadLock` (yani, belge bilgileri ayrıştırılmaya açık olarak açıldığında) çalışır. Daha sonra, belgenin değiştirilmesi gerekiyorsa, kilit zayıf bir **RDT_EditLock**yükseltilir. Kullanıcı belgeyi görünür bir **DocumentWindow**'ta açarsa, `CodeModel` zayıf `RDT_EditLock` olur.  
  
 Kullanıcı daha sonra **DocumentWindow** 'u kapatır ve açık belgeyi kaydetmek isteyip **istemediğiniz sorulduğunda,** `CodeModel` uygulama belgedeki tüm bilgileri atar ve belge için daha fazla bilgi gerektiğinde belgeyi diskten yeniden açar. Bu davranışın alt tlonu, kullanıcının görünmeyen açık belgenin **DocumentWindow** 'u açtığı, değiştirdiği, kapattığı ve sonra belgeyi kaydetmesi istendiğinde **Hayır** ' ı seçtiği bir örneğidir. Bu durumda, belgenin bir olması halinde belge `RDT_ReadLock` aslında kapanmaz ve değiştirilen belge, Kullanıcı belgeyi Kaydetmemeyi tercih etmese de, değiştirilen belge, bellekte açık olarak kalır.  
  
 Belgenin görünmez bir şekilde açılması zayıf bir kullanırsa `RDT_EditLock` , Kullanıcı belgeyi bir daha açıp başka bir kilit tutulmadığında kilidi verir. Kullanıcı **DocumentWindow** 'u kapattığında ve belgeyi kaydetmek isteyip Istemediğiniz sorulduğunda **Hayır** ' ı seçtiğinde, belgenin bellekten kapatılması gerekir. Bu, görünmeyen istemcinin bu oluşumu izlemek için RDT olaylarını dinlemesi gerektiği anlamına gelir. Belge bir dahaki sefer gerekliyse, belgenin yeniden açılması gerekir.
