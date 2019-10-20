---
title: 'Hata &#39;: proje&#39; &#39;projesindeki&#39; bağımlılık dosyası, bağımlılık &#39;dosyası&#39; ile çakışacağından çalıştırma dizinine kopyalanamıyor | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
f1_keywords:
- vs.tasklisterror.copy_version_conflict
ms.assetid: cd7de1eb-7d58-4e2c-9811-a7201f7817be
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5d4fd45741585aaf82c82257999b40d6257e82d9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656043"
---
# <a name="error-the-dependency-39file39-in-project-39project39-cannot-be-copied-to-the-run-directory-because-it-would-conflict-with-dependency-39file39"></a>Hata: &#39;proje&#39; &#39;projesindeki&#39; bağımlılık dosyası, bağımlılık &#39;dosyası ile çakışacağından çalıştırma dizinine kopyalanamıyor&#39;
Başvurular arasında bir çakışma var; uygulamanın çalışması için bin dizinine Kopyalanmakta olan aynı dosya adına sahip birden çok farklı bağımlılık. Bağımlılıkların hiçbiri birincil başvuru olmadığından çalıştırma dizini çakışmayı çözümleyemiyor.

 Bu hata, yapılandırmanın başarısız olmasına neden olur.

 Bu Görev Listesi öğeye çift tıklamak, çakışmayı Çakışmanın oluştuğu projenin Başvurular düğümüne götürür.

 **Bu hatayı düzeltmek için**

- Derlemelerden birini projenizin doğrudan başvurusuyla yapın. Bu yaklaşımın olası bir dezavantajı, seçtiğiniz derlemenin başvurulan derlemenin başka bir sürümünü gerektiren derlemelerle birlikte çalışmak için garanti edilmez.

     \- veya-

- Derlemenin her iki kopyasının de tanımlayıcı olarak adlandırılmış olduğundan ve genel derleme önbelleğinde bulunduğundan emin olun. Bu, derlemeleri bin dizinine kopyalama gereksinimini ortadan kaldırır.

## <a name="see-also"></a>Ayrıca Bkz.
 [Bir proje](../ide/managing-references-in-a-project.md) [genel derleme önbelleğinde](https://msdn.microsoft.com/library/cf5eacd0-d3ec-4879-b6da-5fd5e4372202) başvuruları yönetme [tanımlayıcı-adlandırılmış derlemeler](https://msdn.microsoft.com/library/d4a80263-f3e0-4d81-9b61-f0cbeae3797b) [derleme sürümü oluşturma](https://msdn.microsoft.com/library/775ad4fb-914f-453c-98ef-ce1089b6f903) [nasıl yapılır: Proje bağımlılıklarını oluşturma ve kaldırma](../ide/how-to-create-and-remove-project-dependencies.md)