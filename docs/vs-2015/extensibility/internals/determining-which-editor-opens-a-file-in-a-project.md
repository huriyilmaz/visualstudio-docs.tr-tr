---
title: Bir projede dosya açan düzenleyiciyi belirleme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], determining which editor opens a file
- projects [Visual Studio SDK], determining which editor opens file
- project types, determining which editor opens a file
- persistence, determining which editor opens a file
ms.assetid: acbcf4d8-a53a-4727-9043-696a47369479
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1c79860f770a6b04a17786cfb281fc3c0e4dffda
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196765"
---
# <a name="determining-which-editor-opens-a-file-in-a-project"></a>Projedeki Bir Dosyayı Hangi Düzenleyicinin Açacağını Belirleme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bir Kullanıcı projedeki bir dosyayı açtığında, bu dosya için uygun düzenleyiciyi veya tasarımcıyı açan bir yoklama işleminden geçer. Ortam tarafından çalıştırılan ilk yordam, hem standart hem de özel düzenleyiciler için aynıdır. Ortam, bir dosyayı açmak için kullanılacak düzenleyiciyi yoklayarak ve bu işlem sırasında VSPackage 'ın ortamla birlikte koordine olması gereken çeşitli kriterleri kullanır.  
  
 Örneğin, bir Kullanıcı **Dosya** menüsünden **Aç** komutunu seçerse ve `filename` . rtf (veya. rtf uzantılı başka bir dosya) öğesini seçtiğinde, ortam <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> her bir proje için uygulamayı çağırır, sonunda Çözümdeki tüm proje örnekleri arasında geçiş yapar. Projeler, bir belgedeki talepleri önceliğe göre tanımlayan bir bayrak kümesi döndürür. En yüksek önceliği kullanarak, ortam uygun <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> yöntemi çağırır. Yoklama işlemi hakkında daha fazla bilgi için, [Proje ve proje öğesi şablonları ekleme](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
 Çeşitli dosyalar projesi, diğer projeler tarafından talep edilmeyen tüm dosyaları ister. Bu şekilde, özel düzenleyiciler standart düzenleyiciler onları açmadan önce belgeleri açabilir. Bir Miscellaneous Files projesi bir dosya talep alıyorsa, ortam, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> dosyayı standart bir düzenleyici ile açmak için yöntemini çağırır. Ortam,. rtf dosyalarını işleyen bir tane için kayıtlı düzenleyicilerin iç listesini denetler. Bu liste, kayıt defterinde aşağıdaki anahtarda bulunur:  
  
 [HKEY_LOCAL_MACHINE \Software\Microsoft\VisualStudio \\ < `version`> \Düzenleyiciler \\ {<`editor factory guid`>} \Extensions]  
  
 Ortam Ayrıca bir alt anahtar DocObject 'e sahip herhangi bir nesne için HKEY_CLASSES_ROOT \CLSıD anahtarındaki sınıf tanımlayıcılarını denetler. Dosya Uzantısı orada bulunursa, Microsoft Word gibi uygulamanın katıştırılmış bir sürümü Visual Studio 'da yerinde oluşturulur. Bu belge nesneleri, arabirimini uygulayan bileşik dosyalar olmalıdır <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage> veya nesnenin arabirimi uygulaması gerekir <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> .  
  
 Kayıt defterindeki. rtf dosyaları için bir düzenleyici fabrikası yoksa, ortam HKEY_CLASSES_ROOT \\ . rtf anahtarına bakar ve orada belirtilen düzenleyiciyi açar. Dosya Uzantısı HKEY_CLASSES_ROOT bulunamazsa, ortam, bir metin dosyası ise dosyayı açmak için Visual Studio çekirdek metin düzenleyicisini kullanır.  
  
 Çekirdek metin Düzenleyicisi başarısız olursa, bu durum dosya bir metin dosyası değilse, ortam dosyanın ikili düzenleyicisini kullanır.  
  
 Ortam, kayıt defterinde. rtf uzantısı için bir düzenleyici buluyorsa, bu düzenleyici fabrikası uygulayan VSPackage 'ı yükler. Ortam, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> Yeni VSPackage üzerinde yöntemini çağırır. VSPackage, `QueryService` `SID_SVsRegistorEditor` <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> Düzenleyici fabrikasını ortama kaydetmek için yöntemini kullanarak.  
  
 Ortam şimdi,. rtf dosyaları için yeni kaydedilmiş düzenleyici fabrikası bulmak üzere kayıtlı düzenleyicilerin iç listesini yeniden denetler. Ortam, <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> oluşturmak için dosya adını ve görünüm türünü geçirerek yöntemi uygulamanızı çağırır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>   
 <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>
