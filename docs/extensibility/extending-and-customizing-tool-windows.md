---
title: Araç Windows'u Genişletme ve Özelleştirme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, essentials
- tool windows, standard
ms.assetid: 46b2892e-7b2b-4b3f-83a7-b884f1e114ee
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 76c094ec73a69baa46a5e8313dd26febd57e5887
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711810"
---
# <a name="extend-and-customize-tool-windows"></a>Araç pencerelerini genişletme ve özelleştirme
Visual Studio, araç pencereleri, belge pencereleri ve iletişim pencereleri gibi birkaç farklı türde pencere sağlar. **Özellikler** penceresi, **Çıktı** penceresi ve **Görev Listesi** penceresi gibi diğer pencereler araç penceresi türleridir.

## <a name="tool-windows"></a>Araç pencereleri
 Visual Studio araç pencereleri genellikle dosya tabanlı olmayan salt okunur pencerelerdir. Bu, dosyaları okuma yazma modunda görüntüleyen belge pencerelerinden farklıdır. **Araç Kutusu**, **Çözüm Gezgini**, **Özellikler** penceresi ve **Web Tarayıcısı** araç pencerelerinin örnekleridir.

 Basit bir araç penceresi nin nasıl oluşturulabildiğini öğrenmek için [bkz.](../extensibility/adding-a-tool-window.md)

 Visual Studio'ya bir araç penceresi kaydetmek için [bkz.](../extensibility/registering-a-tool-window.md)

 Araç pencereleri varsayılan olarak tek örneklidir, bu da araç penceresinin yalnızca bir örneğinin aynı anda açılabilir anlamına gelir. Tek örnekli araç penceresi açıldıktan sonra, IDE kapanana kadar açık kalır. Tek örnekli bir araç penceresini kapattığınızda, yalnızca görünürlüğü değişir. Pencerenin birden çok örneğinin aynı anda açılabilir şekilde çok örnekli araç pencereleri de oluşturabilirsiniz. Bkz. Daha fazla bilgi için [çok örnekli araç penceresi oluştur.](../extensibility/creating-a-multi-instance-tool-window.md)

 Araç pencereleri *dinamik*olabilir, yani ilgili UI bağlamları uygulandığında görünür olurlar. Otomatik görünürlük kullanımı, IDE'deki pencerelerin dağınıklığını azaltabilir. Daha fazla bilgi için bkz. [dinamik bir araç penceresi aç.](../extensibility/opening-a-dynamic-tool-window.md)

 Araç pencereleri belge çerçevesine sabitlenebilir, kayar veya sekmeli olabilir. Araç pencere çerçevesi IDE tarafından sağlanır ve boyutu, konumu, yerleştirme durumunu ve diğer kalıcı özellikleri denetlemek için kullanılır. Araç penceresi bölmesi içindekileri görüntüler. Varsayılan boyut ve konum yalnızca araç penceresi ilk açıldığında geçerlidir; bundan sonra araç penceresi durumu devam etti.

 Araç penceresi bölmeleri WPF kullanıcı denetimlerini barındırabilir ve araç çubuklarını destekleyebilir. Barındırılan denetimin tutamacını döndürmek için <xref:Microsoft.VisualStudio.Shell.WindowPane.Window%2A> özelliği geçersiz kılabilirsiniz.

 Araç pencerelerine birçok farklı özellik ekleyebilirsiniz. Örneğin, araç çubuğu ekleyebilirsiniz: [Araç penceresine araç çubuğu](../extensibility/adding-a-toolbar-to-a-tool-window.md) veya kısayol menüsü ekleyin: [Araç penceresinde kısayol menüsü ekleyin.](../extensibility/adding-a-shortcut-menu-in-a-tool-window.md) Araç pencerenizdeki öğeleri aramanızı sağlayan bir Arama denetimi ekleyebilirsiniz: [Araç penceresine arama ekleyin.](../extensibility/adding-search-to-a-tool-window.md)

 Araç penceresi olaylarına abone olabilirsiniz: [Bir etkinliğe abone](../extensibility/subscribing-to-an-event.md)olun.

## <a name="extend-existing-tool-windows"></a>Varolan araç pencerelerini genişletme
 Yeni seçenekler **sayfasına** araç pencereniz hakkında bilgi ve **Özellikler** sayfasındaki yeni bir ayar ekleyebilir, **Görev Listesi** ve **Çıktı** pencerelerine yazabilirsiniz. Daha fazla bilgi için bkz: [Özellikleri Genişlet, Görev Listesi, Çıktı ve Seçenekler penceresi.](../extensibility/extending-the-properties-task-list-output-and-options-windows.md)

## <a name="modal-dialog-boxes"></a>Modal iletişim kutuları
 Visual Studio uzantısı nda, onları ve Kullanıcı Aracı'nın <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow?displayProperty=fullName>geri kalanını kontrol etmenizi sağlayan, modal iletişim kutularını türeterek oluşturmalısınız. Daha fazla bilgi için [modal iletişim kutularını oluştur ve yönet'](../extensibility/creating-and-managing-modal-dialog-boxes.md)e bakın.

## <a name="see-also"></a>Ayrıca bkz.
- [Araç penceresi ile uzantı oluşturma](../extensibility/creating-an-extension-with-a-tool-window.md)
- [Projeleri genişletme](../extensibility/extending-projects.md)
- [Çözümleri genişletin](../extensibility/extending-solutions.md)
