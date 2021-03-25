---
title: Bir projede dosya açan düzenleyiciyi belirleme | Microsoft Docs
description: Bir projede dosya açan düzenleyiciyi anlamak için Visual Studio tarafından kullanılan kayıt defteri anahtarları ve Visual Studio SDK yöntemleri hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], determining which editor opens a file
- projects [Visual Studio SDK], determining which editor opens file
- project types, determining which editor opens a file
- persistence, determining which editor opens a file
ms.assetid: acbcf4d8-a53a-4727-9043-696a47369479
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fb6f142ea25748f6798fb60d7c03862c51819349
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090869"
---
# <a name="determine-which-editor-opens-a-file-in-a-project"></a>Bir projede dosya açan düzenleyiciyi belirleme
Bir Kullanıcı projedeki bir dosyayı açtığında, bu dosya için uygun düzenleyiciyi veya tasarımcıyı açan bir yoklama işleminden geçer. Ortam tarafından çalıştırılan ilk yordam, hem standart hem de özel düzenleyiciler için aynıdır. Ortam, bir dosyayı açmak için kullanılacak düzenleyiciyi yoklayarak ve bu işlem sırasında VSPackage 'ın ortamla birlikte koordine olması gereken çeşitli kriterleri kullanır.

 Örneğin, bir Kullanıcı **Dosya** menüsünden **Aç** komutunu seçip *dosya adı. rtf* (veya *. rtf* uzantılı başka bir dosya) seçeneğini belirlediğinizde, ortam <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> her bir proje için uygulamayı çağırır, sonunda çözüm içindeki tüm proje örnekleri arasında geçiş yapar. Projeler, bir belgedeki talepleri önceliğe göre tanımlayan bir bayrak kümesi döndürür. En yüksek önceliği kullanarak, ortam uygun <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> yöntemi çağırır. Yoklama işlemi hakkında daha fazla bilgi için bkz. [Proje ve proje öğesi şablonları ekleme](../../extensibility/internals/adding-project-and-project-item-templates.md).

 Çeşitli dosyalar projesi, diğer projeler tarafından talep edilmeyen tüm dosyaları ister. Bu şekilde, özel düzenleyiciler standart düzenleyiciler onları açmadan önce belgeleri açabilir. Bir Miscellaneous Files projesi bir dosya talep alıyorsa, ortam, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> dosyayı standart bir düzenleyici ile açmak için yöntemini çağırır. Ortam, *. rtf* dosyalarını işleyen bir tane için kayıtlı düzenleyicilerin iç listesini denetler. Bu liste, kayıt defterinde aşağıdaki anahtarda bulunur:

 **HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\ \<version> \Düzenleyiciler \\ \<editor factory guid> \Extensions**

 Ortam Ayrıca, **DocObject** alt anahtarına sahip herhangi bir nesne için **HKEY_CLASSES_ROOT\CLSID** anahtarındaki sınıf tanımlayıcılarını de denetler. Dosya Uzantısı orada bulunursa, Microsoft Word gibi uygulamanın katıştırılmış bir sürümü Visual Studio 'da yerinde oluşturulur. Bu belge nesneleri, arabirimini uygulayan bileşik dosyalar olmalıdır <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage> veya nesnenin arabirimi uygulaması gerekir <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> .

 Kayıt defterindeki *. rtf* dosyaları için bir düzenleyici fabrikası yoksa, ortam **HKEY_CLASSES_ROOT \\ . rtf** anahtarına bakar ve orada belirtilen düzenleyiciyi açar. Dosya Uzantısı **HKEY_CLASSES_ROOT** bulunamazsa, ortam, bir metin dosyası ise dosyayı açmak Için Visual Studio çekirdek metin düzenleyicisini kullanır.

 Çekirdek metin Düzenleyicisi başarısız olursa, bu durum dosya bir metin dosyası değilse, ortam dosyanın ikili düzenleyicisini kullanır.

 Ortam, kayıt defterinde *. rtf* uzantısı için bir düzenleyici buluyorsa, bu düzenleyici fabrikası uygulayan VSPackage 'ı yükler. Ortam, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> Yeni VSPackage üzerinde yöntemini çağırır. VSPackage, `QueryService` `SID_SVsRegistorEditor` <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> Düzenleyici fabrikasını ortama kaydetmek için yöntemini kullanarak.

 Ortam artık, *. rtf* dosyaları için yeni kaydedilmiş düzenleyici fabrikasını bulmak üzere kayıtlı düzenleyicilerin iç listesini yeniden denetler. Ortam, <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> oluşturmak için dosya adını ve görünüm türünü geçirerek yöntemi uygulamanızı çağırır.

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>
- <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>
