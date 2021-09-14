---
title: Özellikler penceresi düğmeleri | Microsoft Docs
description: Özellikler penceresi araç çubuğunda ve düğmelerin uygulanmasıyla ilgili olarak varsayılan olarak görünen düğmeler hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Properties window, buttons
ms.assetid: bdd2e3a7-ae6e-4e88-be1a-e0e3b7ddbbcc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 25cea6a321fe7cf7365f179fd699553bd32b23e3
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126636126"
---
# <a name="properties-window-buttons"></a>Özellikler Penceresi Düğmeleri
Geliştirme diline ve ürün türüne bağlı olarak, **Özellikler** penceresi için araç çubuğunda bazı düğmeler varsayılan olarak görüntülenir. Her durumda, **kategorilere ayrılan**, **sıralama**, **Özellikler** ve **Özellik sayfaları** düğmeleri görüntülenir. Visual C# ve Visual Basic, **olaylar** düğmesi de görüntülenir. Bazı Visual C++ projelerinde, **vc + + iletileri** ve **vc geçersiz kılmalar** düğmeleri görüntülenir. Diğer proje türleri için ek düğmeler gösterilebilir. **Özellikler** penceresindeki düğmeler hakkında daha fazla bilgi için bkz. [Özellikler penceresi](../../ide/reference/properties-window.md).

## <a name="implementation-of-properties-window-buttons"></a>Özellikler penceresi düğmelerinin uygulanması
 **kategorilere ayrılmış** düğmesine tıkladığınızda, Visual Studio <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> özelliklerini kategoriye göre sıralamak için odağı olan nesne üzerindeki arabirimi çağırır. <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> , `IDispatch` **Özellikler** penceresine sunulan nesnesine uygulanır.

 Negatif değerlere sahip 11 önceden tanımlanmış özellik kategorisi vardır. Özel kategoriler tanımlayabilirsiniz, ancak bunları önceden tanımlanmış kategorilerden ayırt etmek için pozitif değerler atamanızı öneririz.

 <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.MapPropertyToCategory%2A>Yöntemi, belirtilen özellik için uygun özellik kategorisi değerini döndürür. <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.GetCategoryName%2A>Yöntemi, kategori adını içeren bir dize döndürür. yalnızca standart özellik kategorisi değerlerini bildiğinden Visual Studio özel kategori değerleri için destek sağlamanız gerekir.

 **Alfabetik hale getirme** düğmesine tıkladığınızda Özellikler ada göre alfabetik sırada görüntülenir. Adlar, `IDispatch` yerelleştirilmiş bir sıralama algoritmasına göre alınır.

 **Özellikler** penceresi açık olduğunda, **Özellikler** düğmesi otomatik olarak seçili olarak gösterilir. Ortamın diğer bölümlerinde aynı düğme görüntülenir ve **Özellikler** penceresini göstermek için bu düğmeye tıklayabilirsiniz.

 Seçili nesne için uygulanmıyorken **Özellik sayfaları** düğmesi kullanılamaz `ISpecifyPropertyPages` . Özellik sayfaları, genellikle çözümler ve projelerle ilişkili yapılandırmaya bağımlı özellikleri görüntüler, ancak proje öğeleriyle da ilişkilendirilebilirler (örneğin, Visual C++).

> [!NOTE]
> Yönetilmeyen kod kullanarak **Özellikler** penceresine araç çubuğu düğmeleri ekleyemezsiniz. Bir araç çubuğu düğmesi eklemek için, öğesinden türetilmiş bir yönetilen nesne oluşturmalısınız <xref:System.Windows.Forms.Design.PropertyTab> .

## <a name="see-also"></a>Ayrıca bkz.
- [Özellikleri Genişletme](../../extensibility/internals/extending-properties.md)
