---
title: Eski API 'de metin arabelleği olayları | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text buffer events
ms.assetid: 9be49e9f-1864-41c2-8a3c-f66895881341
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e82fa31ca435d0c850a4d9e75e927cff9613b046
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186414"
---
# <a name="text-buffer-events-in-the-legacy-api"></a>Eski API'deki Metin Arabelleği Olayları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Metin arabelleği nesnesi, farklı durumlara yanıt vermenize imkan tanıyan birkaç farklı olay yayar.  
  
 Eski API 'yi kullanırken, metin arabelleğindeki değişiklikler hakkında bildirim almak için aşağıdaki arabirimleri uygulamanız gerekir. `IConnectionPointContainer`Arabellekte satır değişikliklerinin bildirimini almak için metin arabelleğindeki arabirimi kullanarak arabirimleri metin arabelleğine sunun. Daha fazla bilgi için bkz. [nasıl yapılır: eskı API Ile metin arabelleği olaylarını kaydetme](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md). Veya arabirimleri durumunda, `IVsTextStreamEvents` `IVsTextLinesEvents` değişiklikler sırasıyla bir veya iki boyutlu koordinatlarla döndürülür.  
  
## <a name="text-buffer-interfaces"></a>Metin arabelleği arabirimleri  
 Metin arabelleği nesnesi tarafından uygulanan arabirimler aşağıda verilmiştir.  
  
|Arabirim|Açıklama|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Bileşik eylemlerin (yani, tek bir geri alma/yineleme biriminde gruplanmış eylemler) oluşturulmasına izin vermez.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Metin arabelleği tarafından yönetilen belge verilerinin kalıcılığını mümkün hale getirme.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|Temel hizmetleri sağlar; birçok istemci tarafından kullanılır.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|İki boyutlu koordinatları kullanarak okuma ve yazma özellikleri sağlar. Öğesinden devralır `IVsTextBuffer` .|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|Arabellekte metne hızlı, akışa dayalı ve sıralı erişim sağlar.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|Tek boyutlu koordinatları kullanarak okuma ve yazma özellikleri sağlar. Öğesinden devralır `IVsTextBuffer` .|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|Genel bir özellikler koleksiyonuna erişim sağlar. En önemli özellik, arabelleğin adı ya da adıdır. Bir GUID oluşturarak ve anahtar olarak kullanarak kendi rastgele verilerinizi bu arabirimle birlikte depolayabilmeniz gerekir.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|Olaylar için bağlantı noktalarını destekler.|  
  
## <a name="text-buffer-event-interfaces"></a>Metin arabelleği olay arabirimleri  
 Metin arabelleği olay bildirimi için arabirimler aşağıda verilmiştir.  
  
|Arabirim|Açıklama|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferEvents>|Yeni bir dil hizmeti bir metin arabelleğiyle ilişkilendirildiğinde istemcilere bildirir.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferDataEvents>|Bir metin arabelleği başlatıldığında ve metin arabelleğindeki verilerde değişiklik yapıldığında istemcilere bildirir.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamEvents>|Tek boyutlu koordinatlarda, temeldeki metin arabelleğindeki değişiklikleri istemcilere bildirir.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>|İki boyutlu koordinatlarda, temeldeki metin arabelleğindeki değişiklikleri istemcilere bildirir.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserDataEvents>|Kullanıcılara Kullanıcı verilerinde değişiklik olduğunu bildirir.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>|Son kayıt hareketini istemcilerine olayı tetikleyip değiştirilen metin aralığını bildirir. `IVsPreliminaryTextChangeCommitEvents`Geri alma veya yineleme komutlarına yanıt olarak arabirim tetiklenmez. Olaylar yalnızca geri alma yöneticisi olan arabellekler için ateşlenir. `IVsPreliminaryTextChangeCommitEvents` , diğer olayların değişiklikler kaydedilmeden önce metni değiştirmediğinden emin olmak için, düzgün listeleme gibi diğer olaylardan önce tetiklenir. VSPackage uygulamanızın `IVsPreliminaryTextChangeCommitEvents` arabirimini veya arabirimini izlemesi gerekir `IVsFinalTextChangeCommitEvents` , ancak ikisini birden değil.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>|Son kayıt hareketini istemcilerine olayı tetikleyip değiştirilen metin aralığını bildirir. `IVsFinalTextChangeCommitEvents`Geri alma veya yineleme komutlarına yanıt olarak arabirim tetiklenmez. Olaylar yalnızca geri alma yöneticisi olan arabellekler için ateşlenir. `IVsFinalTextChangeCommitEvents` yalnızca dil Hizmetleri tarafından veya düzenlemenin tamamen denetimine sahip diğer nesneler tarafından kullanılmaya yöneliktir. VSPackage uygulamanızın `IVsPreliminaryTextChangeCommitEvents` arabirimini veya arabirimini izlemesi gerekir `IVsFinalTextChangeCommitEvents` , ancak ikisini birden değil.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Eski API kullanarak metin arabelleğine erişme](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)   
 [Nasıl Yapılır: Eski API ile Metin Arabelleği Olaylarına Kaydolma](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)
