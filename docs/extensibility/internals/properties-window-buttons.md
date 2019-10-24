---
title: Özellikler penceresi düğmeleri | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, buttons
ms.assetid: bdd2e3a7-ae6e-4e88-be1a-e0e3b7ddbbcc
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3f2a41917a58a6fc5780b62c2c9e3db8aa52d407
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725266"
---
# <a name="properties-window-buttons"></a>Özellikler Penceresi Düğmeleri
Geliştirme diline ve ürün türüne bağlı olarak, **Özellikler** penceresi için araç çubuğunda bazı düğmeler varsayılan olarak görüntülenir. Her durumda, **kategorilere ayrılan**, **sıralama**, **Özellikler**ve **Özellik sayfaları** düğmeleri görüntülenir. Görsel C# ve Visual Basic, **Olaylar** düğmesi de görüntülenir. Bazı görsel C++ projelerde **VC + + Iletileri** ve **vc geçersiz kılmalar** düğmeleri görüntülenir. Diğer proje türleri için ek düğmeler gösterilebilir. **Özellikler** penceresindeki düğmeler hakkında daha fazla bilgi için bkz. [Özellikler penceresi](../../ide/reference/properties-window.md).

## <a name="implementation-of-properties-window-buttons"></a>Özellikler penceresi düğmelerinin uygulanması
 **Kategorilere ayrılmış** düğmesine tıkladığınızda, Visual Studio nesnenin özelliklerini kategoriye göre sıralamak için odaklı <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> arabirimini çağırır. <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>, **Özellikler** penceresine sunulan `IDispatch` nesnesine uygulanır.

 Negatif değerlere sahip 11 önceden tanımlanmış özellik kategorisi vardır. Özel kategoriler tanımlayabilirsiniz, ancak bunları önceden tanımlanmış kategorilerden ayırt etmek için pozitif değerler atamanızı öneririz.

 <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.MapPropertyToCategory%2A> yöntemi, belirtilen özellik için uygun özellik kategorisi değerini döndürür. <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.GetCategoryName%2A> yöntemi kategori adını içeren bir dize döndürür. Visual Studio standart özellik kategorisi değerlerini bildiğinden, yalnızca özel kategori değerleri için destek sağlamanız gerekir.

 **Alfabetik hale getirme** düğmesine tıkladığınızda Özellikler ada göre alfabetik sırada görüntülenir. Adlar, yerelleştirilmiş bir sıralama algoritmasına göre `IDispatch` tarafından alınır.

 **Özellikler** penceresi açık olduğunda, **Özellikler** düğmesi otomatik olarak seçili olarak gösterilir. Ortamın diğer bölümlerinde aynı düğme görüntülenir ve **Özellikler** penceresini göstermek için bu düğmeye tıklayabilirsiniz.

 Seçili nesne için `ISpecifyPropertyPages` uygulanmıyorken **Özellik sayfaları** düğmesi kullanılamaz. Özellik sayfaları, genellikle çözümlerle ve projelerle ilişkili olan yapılandırmaya bağlı özellikleri görüntüler, ancak proje öğeleriyle da ilişkilendirilebilirler (örneğin, görsel C++).

> [!NOTE]
> Yönetilmeyen kod kullanarak **Özellikler** penceresine araç çubuğu düğmeleri ekleyemezsiniz. Bir araç çubuğu düğmesi eklemek için <xref:System.Windows.Forms.Design.PropertyTab>türetilen bir yönetilen nesne oluşturmalısınız.

## <a name="see-also"></a>Ayrıca bkz.
- [Özellikleri Genişletme](../../extensibility/internals/extending-properties.md)