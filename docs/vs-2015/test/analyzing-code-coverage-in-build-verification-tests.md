---
title: Derleme doğrulama testlerinde kod kapsamını çözümleme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 59c07d15-511e-4fd0-b398-bde9d5ed00d9
caps.latest.revision: 10
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2442bf4cc31eeb51332aa28325924e18ccb1ffb7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660722"
---
# <a name="analyzing-code-coverage-in-build-verification-tests"></a>Derleme Doğrulama Testlerinde Kod Kapsamını Çözümleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Microsoft Visual Studio kod kapsamı analizi, kodunuzun ne kadarının otomatik testler tarafından uygulanmakta olduğunu gösterir. Daha fazla bilgi için bkz. kod [kapsamını kullanarak ne kadar kodun test edildiğini belirleme](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

 Kodunuzda denetlediğinizde, testiniz diğer ekip üyelerinden gelen diğer tüm testlerle birlikte yapı sunucusunda çalışır. (Bu ayarı zaten ayarlamadıysanız, bkz. [Yapı sürecinizdeki testleri çalıştırma](https://msdn.microsoft.com/library/d05743a1-c5cf-447e-bed9-bed3cb595e38).) Tüm projede en güncel ve kapsamlı kapsama görünümünü sağladığından, derleme hizmetindeki kod kapsamını çözümlemek yararlı olur. Otomatik sistem testleri ve geliştirme makinelerinde genellikle çalıştırmadığınız kodlanmış diğer testleri de içerecektir.

1. Takım Gezgini ' de, **derlemeler**' ı açın ve ardından bir yapı tanımı ekleyin veya düzenleyin.

2. **İşlem** sayfasında **otomatik testler**, **test kaynağı**, **çalıştırma ayarları**' nı genişletin. **Çalışma ayarları dosyasının türünü** **kod kapsamı etkin**olarak ayarlayın.

    Birden fazla Test Kaynağı tanımı varsa, her biri için bu adımı yineleyin.

   - <em>Ancak **tür çalışma ayarları dosyası adında bir</em>alan yok*. *

      **Otomatikleştirilmiş testler**altında, **Test derlemesi** ' ni seçin ve satırın sonundaki üç nokta düğmesini **[...]** seçin. **Test çalıştırması Ekle/Düzenle** iletişim kutusunda, **Test Çalıştırıcısı**' nın altında, **Visual Studio Test Çalıştırıcısı**' nı seçin.

   ![Kod kapsamı için derleme tanımı ayarlanıyor](../test/media/codecoverage-plaincc.png "CodeCoverage-plainCC")

   Derleme çalıştıktan sonra, kod kapsamı sonuçları yapı özetinde görüntülenir.

## <a name="see-also"></a>Ayrıca Bkz.
 [Ne Kadar Kodun Test Edildiğini Belirlemek için Kod Kapsamını Kullanma](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)
