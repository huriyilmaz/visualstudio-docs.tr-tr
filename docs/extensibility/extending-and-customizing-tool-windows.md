---
title: Araç İşLerini Genişletme ve Özelleştirme Windows | Microsoft Docs
description: Özellikler penceresi, Çıkış penceresi ve Visual Studio pencere dahil olmak üzere, Görev Listesi araç pencerelerini genişletme ve özelleştirme hakkında Görev Listesi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, essentials
- tool windows, standard
ms.assetid: 46b2892e-7b2b-4b3f-83a7-b884f1e114ee
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 4b09b0101e7bcab1f342a214d4585e9b54979e099decf3295d705a10a68fc1da
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121432910"
---
# <a name="extend-and-customize-tool-windows"></a>Araç pencerelerini genişletme ve özelleştirme
Visual Studio, araç pencereleri, belge pencereleri ve iletişim kutusu pencereleri gibi birkaç farklı tür pencere sağlar. Özellikler penceresi, **Çıkış** penceresi ve **Görev Listesi** pencere  gibi diğer pencereler, araç penceresi türleridir.

## <a name="tool-windows"></a>Araç pencereleri
 Visual Studio araç pencereleri genellikle dosya tabanlı olmayan salt okunur pencerelerdir. Bu, dosyaları okuma-yazma modunda görüntüleyen belge pencerelerinden farklıdır. Araç **Kutusu**, **Çözüm Gezgini**, **Özellikler** penceresi ve Web **Tarayıcısı araç** pencerelerinin örnekleridir.

 Basit bir araç penceresi oluşturma hakkında bilgi için [bkz. Araç penceresi ekleme.](../extensibility/adding-a-tool-window.md)

 Bir araç penceresini Visual Studio için [bkz. Araç penceresi kaydetme.](../extensibility/registering-a-tool-window.md)

 Araç pencereleri varsayılan olarak tek örneklidir, yani araç penceresinin tek bir örneği aynı anda açabilirsiniz. Tek örnekli bir araç penceresi açıldıktan sonra, IDE kapatılana kadar açık kalır. Tek örnekli bir araç penceresini kapatarak yalnızca görünürlüğü değişir. Pencerenin birden çok örneğinin aynı anda açılamayacak şekilde çok örnekli araç pencereleri de oluşturabilirsiniz. Daha [fazla bilgi için bkz. Çok örnekli](../extensibility/creating-a-multi-instance-tool-window.md) araç penceresi oluşturma.

 Araç pencereleri dinamik *olabilir,* yani ilgili kullanıcı arabirimi bağlamı her uygulandığında görünür olur. Otomatik görünürlük kullanımı, IDE'de pencerelerin dağınıklıklarını azaltabilirsiniz. Daha fazla bilgi için [bkz. Dinamik bir araç penceresi açma.](../extensibility/opening-a-dynamic-tool-window.md)

 Araç pencereleri, belge çerçevesine yerleştirildi, kayan veya sekmeyle yerleştirildi. Araç penceresi çerçevesi IDE tarafından sağlanır ve boyutu, konumu, yerleştirme durumunu ve diğer kalıcı özellikleri kontrol etmek için kullanılır. Araç penceresi bölmesinde içerikler görüntülenir. Varsayılan boyut ve konum yalnızca araç penceresi ilk açıldığında geçerlidir; bu durumdan sonra araç penceresi durumu kalıcı olur.

 Araç penceresi bölmeleri WPF kullanıcı denetimlerini ve destek araç çubuklarını barındırabilir. Barındırılan <xref:Microsoft.VisualStudio.Shell.WindowPane.Window%2A> denetimin tanıtıcısı dönmek için özelliğini geçersiz kılabilirsiniz.

 Araç pencerelere birçok farklı özellik eklemek için kullanabilirsiniz. Örneğin, bir araç çubuğu ekleyebilirsiniz: [Araç](../extensibility/adding-a-toolbar-to-a-tool-window.md) penceresine veya kısayol menüsüne araç çubuğu ekleme: [Araç penceresine kısayol menüsü ekleyin.](../extensibility/adding-a-shortcut-menu-in-a-tool-window.md) Araç pencerenizin içinde öğeleri aramanıza olanak sağlayan bir Arama denetimi eklemek için: [Bir araç penceresine arama ekleyin.](../extensibility/adding-search-to-a-tool-window.md)

 Araç penceresi olaylarını abone olabilirsiniz: [Bir etkinliğe abone olun.](../extensibility/subscribing-to-an-event.md)

## <a name="extend-existing-tool-windows"></a>Mevcut araç pencerelerini genişletme
 Araç pencereniz hakkında bilgileri yeni  bir Seçenekler sayfasına ve Özellikler sayfasındaki yeni bir **ayara** ekleyebilir, Görev Listesi **ve Çıkış** **pencerelerini yazabilirsiniz.** Daha fazla bilgi için [bkz. Özellikler, Görev Listesi, Çıkış ve Seçenekler pencerelerini genişletme.](../extensibility/extending-the-properties-task-list-output-and-options-windows.md)

## <a name="modal-dialog-boxes"></a>Kalıcı iletişim kutuları
 Bir Visual Studio' uzantısında, bunları ve kullanıcı arabiriminin geri kalanını denetlemeye olanak sağlayan 'den türeterek <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow?displayProperty=fullName> kalıcı iletişim kutuları oluşturmanız gerekir. Daha fazla bilgi için [bkz. Kalıcı iletişim kutuları oluşturma ve yönetme.](../extensibility/creating-and-managing-modal-dialog-boxes.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Araç penceresiyle uzantı oluşturma](../extensibility/creating-an-extension-with-a-tool-window.md)
- [Projeleri genişletme](../extensibility/extending-projects.md)
- [Çözümleri genişletme](../extensibility/extending-solutions.md)
