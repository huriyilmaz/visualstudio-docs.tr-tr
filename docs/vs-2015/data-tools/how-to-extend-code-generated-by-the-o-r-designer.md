---
title: 'Nasıl yapılır: O-R Tasarımcısı tarafından oluşturulan kodu genişletme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: d6d1122e-2f55-4607-8d8b-48c3c22600fb
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a1d60090ca16907e16bb58970d793124c5bb2dec
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665955"
---
# <a name="how-to-extend-code-generated-by-the-or-designer"></a>Nasıl yapılır: O/R Tasarımcısı tarafından oluşturulan kodu genişletme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

@No__t_0 tarafından oluşturulan kod, varlık sınıflarında ve tasarımcı yüzeyinde diğer nesnelerde değişiklik yapıldığında yeniden oluşturulur. Bu kod yeniden oluşturma nedeniyle, tasarımcı kodu yeniden oluştururken oluşturulan koda eklediğiniz tüm kodlar genellikle üzerine yazılır. @No__t_0, üzerine yazılmayacak kodu ekleyebileceğiniz kısmi sınıf dosyaları oluşturma yeteneği sağlar. Kendi kodunuzu [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] tarafından oluşturulan koda eklemenin bir örneği, LINQ to SQL (varlık) sınıflarına veri doğrulaması eklemektir. Bilgi için bkz. [nasıl yapılır: varlık sınıflarına doğrulama ekleme](../data-tools/how-to-add-validation-to-entity-classes.md).

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

## <a name="adding-code-to-an-entity-class"></a>Bir varlık sınıfına kod ekleme

#### <a name="to-create-a-partial-class-and-add-code-to-an-entity-class"></a>Kısmi bir sınıf oluşturmak ve bir varlık sınıfına kod eklemek için

1. @No__t_1 yeni bir LINQ to SQL Classes dosyası ( **. dbml** dosyası) açın veya oluşturun. ( **Çözüm Gezgini** /**veritabanı Gezgini** **. dbml** dosyasına çift tıklayın.)

2. @No__t_0, doğrulama eklemek istediğiniz sınıfa sağ tıklayın ve sonra **kodu görüntüle**' ye tıklayın.

     Kod Düzenleyicisi seçili varlık sınıfı için kısmi bir sınıf ile açılır.

3. Varlık sınıfı için kısmi sınıf bildiriminde kodunuzu ekleyin.

## <a name="adding-code-to-a-datacontext"></a>DataContext 'e kod ekleme

#### <a name="to-create-a-partial-class-and-add-code-to-a-datacontext"></a>Kısmi bir sınıf oluşturmak ve DataContext 'e kod eklemek için

1. @No__t_1 yeni bir LINQ to SQL Classes dosyası ( **. dbml** dosyası) açın veya oluşturun. ( **Çözüm Gezgini** /**veritabanı Gezgini** **. dbml** dosyasına çift tıklayın.)

2. @No__t_0 tasarımcıda boş bir alana sağ tıklayın ve ardından **kodu görüntüle**' ye tıklayın.

     Kod Düzenleyicisi DataContext için kısmi bir sınıf ile açılır.

3. DataContext için kısmi sınıf bildiriminde kodunuzu ekleyin.

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio 'da LINQ to SQL araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [izlenecek yol: LINQ to SQL sınıfları oluşturma (O-R Designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [izlenecek yol: varlık sınıflarına doğrulama ekleme](https://msdn.microsoft.com/library/85b06a02-b2e3-4534-95b8-d077c8d4c1d7)
