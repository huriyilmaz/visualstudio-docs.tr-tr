---
title: 'Uyarı: &#39;proje&#39; &#39;projesindeki&#39; bağımlılık dosyası, başvuru &#39;dosyasının üzerine yazabileceğinden, çalıştırma dizinine kopyalanamıyor. &#39; | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
f1_keywords:
- vs.tasklisterror.copy_version_warning
ms.assetid: 116819f3-a4d4-48b5-9e71-7c54660d38ef
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a619168bd07fde5d27e5c3d87dc46f505cf5268d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672814"
---
# <a name="warning-the-dependency-39file39-in-project-39project39-cannot-be-copied-to-the-run-directory-because-it-would-overwrite-the-reference-39file39"></a>Uyarı: &#39;proje&#39; &#39;projesindeki&#39; bağımlılık dosyası, başvuru &#39;dosyasının üzerine yazabileceğinden, çalıştırma dizinine kopyalanamıyor.&#39;
Bağımlılıklar arasında bir çakışma vardır; uygulamanın çalışması için aynı ada sahip birden fazla ayrı derleme dosyası, bin dizinine kopyalanmalıdır. Bağımlılıklardan biri birincil başvuru olduğundan, çalıştırma dizini çakışmayı çözümleyebilir.

 Bu Görev Listesi öğeye çift tıklamak sizi çakışan birincil başvuru düğümüne götürür.

 Bu uyarı, bir bağımlılık çakışmasından sahipseniz ancak çakışan bağımlılıklardan birini bir başvuru olarak ekleyerek bu sorunu çözebilirsiniz. Ya da sürüm 1 başvurunuz olabilir ve ardından ilk başvurunun 2. sürümüne başvuran ikinci bir başvuru eklediniz.

 Diğer bir deyişle, çözümünüzdeki projelerin birbirlerine başvuruları olduğundan, bu hata oluşur, ancak başvurular proje için proje yerine dosya başvuruları olarak oluşturulmuştur ( [Başvuru Ekle](https://msdn.microsoft.com/2feb0fe2-0805-4cc9-8cba-b0315849dfb7) Iletişim kutusundaki **tarayıcı** düğmesi kullanılarak) başvurular ( **Başvuru Ekle** Iletişim kutusundaki **Proje** sekmesini kullanarak). Projenin proje başvurusuna avantajı, derleme sistemindeki projeler arasında bir bağımlılık oluşturduğundan, bağımlı projenin, başvuran projenin oluşturulduğu son derlemeden sonra değişmesi durumunda oluşturulması gerekir. Bir dosya başvurusu, bir derleme bağımlılığı oluşturmaz, bu nedenle, bağımlı proje oluşturmadan başvuran projeyi derlemek mümkün olur ve bu nedenle bir başvuru artık kullanılmıyor olabilir; bir proje, projenin daha önce oluşturulmuş bir sürümüne başvurabilir. Bu durum, bin dizininde tek bir DLL 'nin gerekli olmasının, mümkün olmayan ve bu hata iletisi ile sonuçlanmasına neden olabilir.

 Bu ileti bin dizininde bir çakışma olduğunda görüntülenir ve uygulama düzgün çalışmayabilir. Bu sorunu geçici olarak görseniz bile, proje sistemi bir bağımlılık sürümünün tüm bileşenlerle doğru şekilde çalışıp çalışmadığını belirleyemediği için bu uyarı yine de görüntülenir.

 **Bu hatayı düzeltmek için**

- Bir (veya sıfır) bütünleştirilmiş kod dosyasını bin dizinine kopyalayın ve bu, derleme dosyaları genel derleme önbelleğine yerleştirilerek yapılabilir. Genel derleme önbelleği, dosya adı çakışmalarını çözer. Ortak dil çalışma zamanı, genel derleme önbelleğinde derlemelerin nasıl bulunacağını bildiğinden, derleme dosyasının yerel kopyası yapılamaz. Daha fazla bilgi için bkz. [derlemeler ve genel derleme önbelleği Ile çalışma](https://msdn.microsoft.com/library/8a18e5c2-d41d-49ef-abcb-7c27e2469433) ve [hata: ' proje ' projesindeki ' dosya ' bağımlılığı, ' File ' bağımlılığı ile çakışacağından çalıştırma dizinine kopyalanamıyor](/visualstudio/misc/error-dependency-file?view=vs-2015).

## <a name="see-also"></a>Ayrıca Bkz.
 [Bir proje](../ide/managing-references-in-a-project.md) [genel derleme önbelleğinde](https://msdn.microsoft.com/library/cf5eacd0-d3ec-4879-b6da-5fd5e4372202) başvuruları yönetme [nasıl yapılır: Proje bağımlılıklarını oluşturma ve kaldırma](../ide/how-to-create-and-remove-project-dependencies.md)