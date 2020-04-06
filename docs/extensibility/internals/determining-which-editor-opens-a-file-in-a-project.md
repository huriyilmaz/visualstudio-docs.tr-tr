---
title: Projede Hangi Düzenleyicinin Dosya Açtığını Belirleme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], determining which editor opens a file
- projects [Visual Studio SDK], determining which editor opens file
- project types, determining which editor opens a file
- persistence, determining which editor opens a file
ms.assetid: acbcf4d8-a53a-4727-9043-696a47369479
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af7037a3b4bfbae1801e802256af240d017d2789
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708655"
---
# <a name="determine-which-editor-opens-a-file-in-a-project"></a>Projede dosyayı hangi düzenleyicinin açtığını belirleme
Bir kullanıcı projede bir dosya açtığında, ortam bir yoklama işleminden geçerek bu dosya için uygun düzenleyiciyi veya tasarımcıyı açar. Ortam tarafından kullanılan ilk yordam hem standart hem de özel editörler için aynıdır. Ortam, bir dosyayı açmak için hangi düzenleyicinin kullanılacağını yoklarken çeşitli ölçütler kullanır ve VSPackage bu işlem sırasında ortamla koordine edilmelidir.

 Örneğin, bir kullanıcı **Dosya** menüsünden **Aç** komutunu seçip *sonra filename.rtf'yi* (veya *.rtf* uzantılı <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> başka bir dosyayı) seçtiğinde, ortam her proje için uygulamayı çağırır ve sonunda çözümdeki tüm proje örnekleri arasında geçiş yapabilir. Projeler, belgedeki talepleri önceliğe göre tanımlayan bir bayrak kümesi döndürür. En yüksek önceliği kullanarak, ortam <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> uygun yöntemi çağırır. Yoklama işlemi hakkında daha fazla bilgi için [bkz.](../../extensibility/internals/adding-project-and-project-item-templates.md)

 Çeşitli Dosyalar projesi, diğer projeler tarafından talep edilmeyen tüm dosyaları talep ediyor. Bu şekilde, özel düzenleyiciler belgeleri standart düzenleyiciler açmadan önce açabilir. Çeşitli Dosyalar projesi bir dosya talep ederse, ortam dosyayı <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> standart bir düzenleyiciyle açma yöntemini çağırır. Ortam, *.rtf* dosyalarını işleyen bir tane için kayıtlı düzenleyicilerin dahili listesini denetler. Bu liste aşağıdaki anahtarda kayıt defterinde yer alır:

 **HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\\<sürümü>\Editörler\\\<düzenleyici fabrika guid>\Extensions**

 Ortam ayrıca **HKEY_CLASSES_ROOT\CLSID** anahtarındaki sınıf tanımlayıcılarını da denetler. **DocObject** Dosya uzantısı burada bulunursa, Uygulamanın Microsoft Word gibi katıştırılmış bir sürümü Visual Studio'da yerinde oluşturulur. Bu belge nesneleri <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage> arabirimi uygulayan bileşik dosyalar olmalıdır veya <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> nesne arabirimi uygulamalıdır.

 Kayıt defterinde *.rtf* dosyaları için editör fabrikası yoksa, ortam **HKEY_CLASSES_ROOT\\.rtf** anahtarına bakar ve burada belirtilen düzenleyiciyi açar. Dosya uzantısı **HKEY_CLASSES_ROOT'da**bulunmazsa, ortam bir metin dosyasıysa dosyayı açmak için Visual Studio çekirdek metin düzenleyicisini kullanır.

 Çekirdek metin düzenleyicisi başarısız olursa, dosya bir metin dosyası değilse oluşur, ortam dosya için ikili düzenleyicisini kullanır.

 Ortam kayıt defterinde *.rtf* uzantısı için bir düzenleyici bulursa, bu düzenleyici fabrikasını uygulayan VSPackage'ı yükler. Ortam, yeni <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> VSPackage'daki yöntemi çağırır. VSPackage, `QueryService` düzenleyici `SID_SVsRegistorEditor`fabrikayı <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> çevreye kaydettirmek için yöntemi kullanarak çağrıda bulunur.

 Ortam şimdi *.rtf* dosyaları için yeni kayıtlı düzenleyici fabrikasını bulmak için kayıtlı editörlerin dahili listesini yeniden denetler. Ortam, oluşturmak için <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> dosya adı ve görünüm türünü geçerek yöntemin uygulanmasını çağırır.

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>
- <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>
