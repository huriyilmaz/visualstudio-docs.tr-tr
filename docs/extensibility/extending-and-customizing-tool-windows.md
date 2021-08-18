---
title: Araç Windows genişletme ve özelleştirme | Microsoft Docs
description: Özellikler penceresi, çıkış penceresi ve Görev Listesi penceresi dahil Visual Studio sağladığı araç pencerelerini genişletme ve özelleştirme hakkında bilgi edinin.
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
ms.openlocfilehash: 182a1816e692277aa214b8682e6137b515784d29
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122152412"
---
# <a name="extend-and-customize-tool-windows"></a>Araç pencerelerini genişletme ve özelleştirme
Visual Studio, araç pencereleri, belge pencereleri ve iletişim kutusu pencereleri gibi birçok farklı pencere türü sağlar. **Özellikler** penceresi, **çıkış** penceresi ve **görev listesi** penceresi gibi diğer pencereler araç pencerelerinin türleridir.

## <a name="tool-windows"></a>Araç pencereleri
 Visual Studio araç pencereleri genellikle dosya tabanlı olmayan salt okunurdur. Bu, dosyaları okuma-yazma modunda görüntüleyen belge pencerelerini birbirinden farklıdır. **Araç kutusu**, **Çözüm Gezgini**, **Özellikler** penceresi ve **Web tarayıcısı** , araç pencerelerinin örnekleridir.

 Basit bir araç penceresi oluşturmayı öğrenmek için bkz. [araç penceresi ekleme](../extensibility/adding-a-tool-window.md).

 bir araç penceresini Visual Studio kaydetmek için bkz. [bir araç penceresi kaydetme](../extensibility/registering-a-tool-window.md).

 Araç pencereleri, varsayılan olarak tek örnekli, yani araç penceresinin yalnızca bir örneğinin aynı anda açık olması anlamına gelir. Tek örnekli bir araç penceresi açıldıktan sonra, IDE kapatılıncaya kadar açık kalır. Tek örnekli bir araç penceresini kapattığınızda yalnızca görünürlük değişir. Aynı zamanda birden çok örnekli araç penceresi de oluşturabilirsiniz. bu şekilde pencerenin birden çok örneği aynı anda açılabilir. Daha fazla bilgi için bkz. [çok örnekli araç penceresi oluşturma](../extensibility/creating-a-multi-instance-tool-window.md) .

 Araç pencereleri *dinamik* olabilir, yani ilgili Kullanıcı arabirimi bağlamları her geçerliyse görünür hale gelir. Otomatik görünürlük kullanımı IDE 'deki Windows 'un dağınıklığını azaltabilir. Daha fazla bilgi için bkz. [dinamik araç penceresi açma](../extensibility/opening-a-dynamic-tool-window.md).

 Araç pencereleri belge çerçevesinde yerleştirilebilir, kayan veya sekmeli olabilir. Araç penceresi çerçevesi IDE tarafından sağlanır ve boyut, konum, yerleştirme durumu ve diğer kalıcı özellikleri denetlemek için kullanılır. Araç penceresi bölmesi içeriği görüntüler. Varsayılan boyut ve konum yalnızca araç penceresi ilk açıldığında geçerlidir; araç penceresi durumu kalıcı olduktan sonra.

 Araç penceresi bölmeleri, WPF Kullanıcı denetimleri ve destek araç çubuklarını barındırabilir. <xref:Microsoft.VisualStudio.Shell.WindowPane.Window%2A>Barındırılan denetimin tanıtıcısını döndürmek için özelliği geçersiz kılabilirsiniz.

 Araç pencerelerini birçok farklı özellik ekleyebilirsiniz. Örneğin, bir araç çubuğu ekleyebilirsiniz: araç penceresine veya kısayol menüsüne bir [araç çubuğu](../extensibility/adding-a-toolbar-to-a-tool-window.md) ekleme: araç [penceresine kısayol menüsü](../extensibility/adding-a-shortcut-menu-in-a-tool-window.md)ekleme. Araç pencerenizin içindeki öğeleri aramanıza olanak tanıyan bir arama denetimi ekleyebilirsiniz: [bir araç penceresine arama ekleme](../extensibility/adding-search-to-a-tool-window.md).

 Araç penceresi olaylarına abone olabilirsiniz: [bir olaya abone olma](../extensibility/subscribing-to-an-event.md).

## <a name="extend-existing-tool-windows"></a>Var olan araç pencerelerini Genişlet
 Araç pencereniz hakkındaki bilgileri yeni bir **Seçenekler** sayfasına ve **Özellikler** sayfasında yeni bir ayara, **görev listesi** ve **Çıkış** pencerelerini yazmanız için ekleyebilirsiniz. Daha fazla bilgi için bkz. [Özellikleri, görev listesi, çıktıyı ve seçenekler pencerelerini genişletme](../extensibility/extending-the-properties-task-list-output-and-options-windows.md).

## <a name="modal-dialog-boxes"></a>Kalıcı iletişim kutuları
 Visual Studio uzantısında <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow?displayProperty=fullName> , bunları ve kullanıcı arabiriminin geri kalanını denetlemenize olanak tanıyan, öğesinden türeterek kalıcı iletişim kutuları oluşturmanız gerekir. Daha fazla bilgi için bkz. [kalıcı iletişim kutuları oluşturma ve yönetme](../extensibility/creating-and-managing-modal-dialog-boxes.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Araç penceresi ile uzantı oluşturma](../extensibility/creating-an-extension-with-a-tool-window.md)
- [Projeleri genişletme](../extensibility/extending-projects.md)
- [Çözümleri genişletme](../extensibility/extending-solutions.md)
