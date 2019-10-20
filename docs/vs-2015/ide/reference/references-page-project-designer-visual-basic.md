---
title: Başvurular sayfası, proje Tasarımcısı (Visual Basic) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesReference
- vb.ProjectPropertiesUnusedReference
- vb.ProjectPropertiesReferencePaths
helpviewer_keywords:
- References page in Project Designer
- Project Designer, References page
- Unused References dialog box
ms.assetid: 5a47c595-e084-401c-86e1-74e0bf74fd86
caps.latest.revision: 40
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8bb18ec8dd12431d650d844e3698c1986c8d8bd8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665638"
---
# <a name="references-page-project-designer-visual-basic"></a>Başvurular Sayfası, Proje Tasarımcısı (Visual Basic)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Projenizdeki başvuruları, Web başvurularını ve içeri aktarılan ad alanlarını yönetmek için **Proje Tasarımcısı** ' nın **Başvurular** sayfasını kullanın. Projeler COM bileşenleri, XML Web Hizmetleri, .NET Framework sınıf kitaplıkları veya derlemeler ya da diğer sınıf kitaplıkları için başvurular içerebilir. Başvuruları kullanma hakkında daha fazla bilgi için bkz. [bir projedeki başvuruları yönetme](../../ide/managing-references-in-a-project.md).

 **Başvurular** sayfasına erişmek için **Çözüm Gezgini**' de bir proje düğümü ( **çözüm** düğümünü değil) seçin. Ardından, menü çubuğunda **Proje**, **Özellikler** ' i seçin. Proje Tasarımcısı göründüğünde, **Başvurular** sekmesine tıklayın.

## <a name="uielement-list"></a>UIElement Listesi
 Aşağıdaki seçenekler, projenizdeki başvuruları ve içeri aktarılan ad alanlarını seçmenizi veya kaldırmanızı sağlar.

 **Kullanılmayan başvurular** **Kullanılmayan başvurular** iletişim kutusuna erişmek için bu düğmeye tıklayın.

 **Kullanılmayan başvurular** iletişim kutusu, projenizde bulunan ancak kod tarafından gerçekten kullanılmayan başvuruları kaldırmanıza olanak tanır. Bu, **başvuru adını**, **yolu**ve projenizde kullanılmayan ad alanı başvuruları hakkında diğer bilgileri listeleyen bir kılavuz içerir. Kılavuzda, projenizden kaldırmak istediğiniz ad alanı başvurularını seçin ve **Kaldır**' a tıklayın.

 **Başvuru yolları** **Başvuru yolları** iletişim kutusuna erişmek için bu düğmeye tıklayın.

> [!NOTE]
> Proje sistemi bir derleme başvurusu bulduğunda, sistem aşağıdaki konumlara bakarak başvuruyu aşağıdaki sırayla çözümler:
>
> 1. Proje klasörü. **Tüm dosyalar** etkin olmadığında proje klasörü dosyaları **Çözüm Gezgini** görüntülenir.
>    2. **Başvuru yolları** iletişim kutusunda belirtilen klasörler.
>    3. **Başvuru Ekle** iletişim kutusunda dosyaları görüntüleyen klasörler.
>    4. Projenin obj klasörü. (Projenize bir COM başvurusu eklediğinizde, projenin obj klasörüne bir veya daha fazla derleme eklenebilir.)

 **Başvurular** Bu liste, projede kullanılan veya kullanılmayan tüm başvuruları gösterir.

 **Ekle** **Başvurular** listesine bir başvuru veya Web başvurusu eklemek için bu düğmeye tıklayın.

 Başvuru Ekle iletişim kutusunu kullanarak projenize başvuru eklemek için **başvuru** ' yı seçin.

 Web başvurusu Ekle iletişim kutusunu kullanarak projenize Web başvurusu eklemek için **Web başvurusu** ' nu seçin.

 **Kaldır** **Başvurular** listesinde bir veya daha fazla başvuru seçin, sonra silmek için bu düğmeye tıklayın.

 **Web başvurusunu Güncelleştir** **Başvurular** listesinde bir Web başvurusu seçin ve güncelleştirmek için bu düğmeye tıklayın.

 **Içeri aktarılan ad alanları** Kendi ad alanınızı bu kutuya yazabilir ve **Kullanıcı Içeri aktarma Ekle** ' ye tıklayarak ad alanları listesine ekleyebilirsiniz.

 Kullanıcı tarafından içeri aktarılan ad alanları için diğer adlar oluşturabilirsiniz. Bunu yapmak için *diğer adı ve ad alanını = ad* *alanına*girin. Bu, uzun ad alanları kullanıyorsanız faydalıdır, örneğin: `Http= MyOrg.ObjectLib.Internet.WebRequestMethods.Http`.

 **Kullanıcı Içeri aktarma Ekle** **Içeri aktarılan ad alanları** kutusunda belirtilen ad alanını içeri aktarılan ad alanları listesine eklemek için bu düğmeye tıklayın. Düğme, yalnızca belirtilen ad alanı listede yoksa etkindir.

 **Ad alanı listesi** Bu liste tüm kullanılabilir ad alanlarını gösterir. Projenize dahil olan ad alanları için onay kutuları seçilidir.

 **Kullanıcı Içeri aktarmayı Güncelleştir** Ad alanları listesinde Kullanıcı tarafından belirtilen bir ad alanı seçin, **Içeri aktarılan ad alanları** kutusuna değiştirmek istediğiniz adı yazın ve ardından yeni ad alanına geçmek için bu düğmeye tıklayın. Düğme, yalnızca seçilen ad alanı, **Kullanıcı Içeri aktarma Ekle** düğmesini kullanarak listeye eklediğiniz bir ise etkindir. Şunları ekleyebilirsiniz:

- @No__t_0 gibi sınıflar veya ad alanları.

- @No__t_0 gibi diğer ad almalar.

- @No__t_0 gibi XML ad alanları.

## <a name="see-also"></a>Ayrıca Bkz.
 [Nib nasıl yapılır: Başvuru Ekle Iletişim kutusunu kullanarak başvuru ekleme veya kaldırma](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9) [nasıl yapılır: Içeri aktarılan ad alanlarını ekleme veya kaldırma (Visual Basic)](../../ide/how-to-add-or-remove-imported-namespaces-visual-basic.md) [nib: Web başvurusu ekleme Iletişim kutusu](https://msdn.microsoft.com/bdf05776-c591-40af-bfd7-e1e2aa1e87b5) [Imports (XML ad alanı)](https://msdn.microsoft.com/library/1f4d50a6-08c7-4c2e-8206-ccae35fcd1b4)
