---
title: Özellikler Pencere Düğmeleri | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, buttons
ms.assetid: bdd2e3a7-ae6e-4e88-be1a-e0e3b7ddbbcc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aaa4db159ccb0ecf3d0e9c9243e23fcd0dacc455
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706168"
---
# <a name="properties-window-buttons"></a>Özellikler Penceresi Düğmeleri
Geliştirme diline ve ürün türüne bağlı olarak, **Özellikler** penceresinin araç çubuğunda varsayılan olarak belirli düğmeler görüntülenir. Her durumda, **Kategorilere,** **Alfabetik,** **Özellikler**ve **Özellik Sayfaları** düğmeleri görüntülenir. Visual C# ve Visual Basic'te **Olaylar** düğmesi de görüntülenir. Bazı Visual C++ **projelerinde, VC++ İletileri** ve **VC Geçersiz Kılma** düğmeleri görüntülenir. Diğer proje türleri için ek düğmeler görüntülenebilir. **Özellikler** penceresindeki düğmeler hakkında daha fazla bilgi için [Özellikler Penceresi'ne](../../ide/reference/properties-window.md)bakın.

## <a name="implementation-of-properties-window-buttons"></a>Özellikler Pencere Düğmelerinin Uygulanması
 **Kategorilere Ayır düğmesini** tıklattığınızda, <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> Visual Studio özelliklerini kategoriye göre sıralamak için odaklanmış nesneüzerinde arabirimi çağırır. <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>`IDispatch` **Özellikler** penceresine sunulan nesne üzerinde uygulanır.

 Negatif değerlere sahip 11 önceden tanımlanmış özellik kategorisi vardır. Özel kategoriler tanımlayabilirsiniz, ancak bunları önceden tanımlanmış kategorilerden ayırmak için bunları pozitif değerler atamanızı öneririz.

 Yöntem, <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.MapPropertyToCategory%2A> belirtilen özellik için uygun özellik kategori değerini döndürür. Yöntem, <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.GetCategoryName%2A> kategori adını içeren bir dize döndürür. Visual Studio standart özellik kategorisi değerlerini bildiğinden, yalnızca özel kategori değerleri için destek sağlamanız gerekir.

 **Alfabetik** düğmeyi tıklattığınızda, özellikler ada göre alfabetik sırada görüntülenir. Adlar yerelleştirilmiş `IDispatch` bir sıralama algoritmasına göre alınır.

 **Özellikler** penceresi açıldığında, **Özellikler** düğmesi otomatik olarak seçili olarak gösterilir. Ortamın diğer bölümlerinde, aynı düğme görüntülenir ve **Özellikler** penceresini göstermek için düğmeyi tıklatabilirsiniz.

 Seçili nesne için uygulanmazsa **Özellik Sayfaları** düğmesi kullanılamaz. `ISpecifyPropertyPages` Özellik sayfaları genellikle çözümler ve projelerle ilişkili yapılandırmaya bağımlı özellikleri görüntüler, ancak proje öğeleriyle de ilişkilendirilebilir (örneğin, Visual C++'da).

> [!NOTE]
> Yönetilmeyen kodu kullanarak **Özellikler** penceresine araç çubuğu düğmeleri ekleyemezsiniz. Araç çubuğu düğmesi eklemek için, 'den <xref:System.Windows.Forms.Design.PropertyTab>türetilen yönetilen bir nesne oluşturmanız gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Özellikleri Genişletme](../../extensibility/internals/extending-properties.md)
