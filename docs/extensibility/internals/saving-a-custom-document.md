---
title: Özel Belge Kaydetme | Microsoft Docs
description: IDE'ye ek olarak proje türü için özel bir belge için oluşan işlem hakkında Visual Studio öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, saving custom documents
- projects [Visual Studio SDK], saving custom documents
- editors [Visual Studio SDK], saving custom documents
ms.assetid: 040b36d6-1f0a-4579-971c-40fbb46ade1d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 262bc240ab9a73c500fcb59e2796c42c50a7479d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122049603"
---
# <a name="saving-a-custom-document"></a>Özel Belge Kaydetme
Ortam Save , **Save** **As** ve Save **All komutlarını** işlemektedir. Kullanıcı Dosya menüsünde **Kaydet,** **Farklı** **Kaydet** veya  Hepsini Kaydet'e tıkladığında ya da çözümü kapatarak Hepsini Kaydet'e tıkladığında, aşağıdaki işlem gerçekleşir.

 ![Müşteri Düzenleyicisi Kaydetme](../../extensibility/internals/media/private.gif "Özel") Özel bir düzenleyici için Kaydet, Farklı Kaydet ve Tüm komut işlemeyi kaydet

 Bu işlem aşağıdaki adımlarda ayrıntılı olarak açıktır:

1. Farklı **Kaydet** ve **Farklı Kaydet** komutları için ortam, etkin belge penceresini ve bu nedenle hangi öğelerin kaydedilmiş olması gerektiğini belirlemek üzere <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> hizmeti kullanır. Etkin belge penceresi bilindiği zaman ortam, çalışan belge tablosunda belgenin hiyerarşi işaretçisini ve öğe tanımlayıcısını (itemID) bulur. Daha fazla bilgi için [bkz. Belge Tablosu Çalıştırma.](../../extensibility/internals/running-document-table.md)

     Tüm Öğeleri Kaydet komutu için ortam, kaydedilen tüm öğelerin listesini derlemek için çalışan belge tablosunda yer alan bilgileri kullanır.

2. Çözüm bir çağrı aldığında, seçilen öğe kümesinde (yani hizmet tarafından ortaya çıkarıla birden çok <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> seçim) boyunca devam <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> eder.

3. Seçimde yer alan her öğede çözüm, Kaydet menü komutunun etkin olup olmadığını belirlemek üzere <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> yöntemini çağıran hiyerarşi işaretçisini kullanır. Bir veya daha fazla öğe kirli ise Kaydet komutu etkinleştirilir. Hiyerarşi standart bir düzenleyici kullanıyorsa, hiyerarşi yöntemini çağırarak kirli durum sorgulamayı düzenleyiciye <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> devreder.

4. Kirli olan her seçili öğede çözüm, uygun hiyerarşilerde yöntemini <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> çağıran hiyerarşi işaretçisini kullanır.

     Özel düzenleyicide, belge veri nesnesi ile proje arasındaki iletişim özeldir. Bu nedenle, bu iki nesne arasında özel kalıcılık sorunları ele alınan.

    > [!NOTE]
    > Kendi kalıcılığınızı uygulayacaksanız, zaman kazanmak için yöntemini <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> çağırdığını emin olun. Bu yöntem, dosyayı kaydetmenin güvenli olduğundan emin olmak için denetler (örneğin, dosya salt okunur değildir).

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Proje Öğelerini Açma ve Kaydetme](../../extensibility/internals/opening-and-saving-project-items.md)
