---
title: 'Nasıl yapılır: menü öğesini kullanarak uyarıları bastırma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- warnings, suppressing
- code analysis, suppressing warnings
ms.assetid: 36bd1850-dcde-4ed0-9bc3-0b83df434362
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 96b7433ff4f696989142aa2c2ce47982006b93b2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72610022"
---
# <a name="how-to-suppress-warnings-by-using-the-menu-item"></a>Nasıl yapılır: Menü Öğesini Kullanarak Uyarıları Bastırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

NOTUN
> Kaynak gizleme bölümünde Web sitesi projelerinde desteklenmez.

 Kod Analizi uyarılarını bastırmak için kod analizi penceresini kullanabilirsiniz. Bir uyarının gizlenmesi, devre dışı bırakmayla aynı değildir. Bir uyarıyı bastırdığınızda, bu yalnızca ihlalin belirli bir örneği için geçerlidir. Aynı uyarıya ilişkin diğer ihlaller de Hata Listesi penceresinde bildirilmeyecektir.

 Kod analizini çalıştırdıktan sonra, Kod Analizi penceresinde görüntülenen bir veya daha fazla kod analizi uyarısı uygulamanız için geçerli değildir. Örneğin, kodun olduğu gibi doğru olduğunu tespit edebilirsiniz. Ya da bazı ihlallerin düşük öncelikli olması ve geçerli geliştirme sürecinde düzeltilmeyecek olması olabilir. Nedeninden bağımsız olarak, takım üyelerinizin kodun incelendiğini ve uyarının bastırıldığına ilişkin olduğunu bilmesini sağlamak için uyarının uygulanamaz olduğunu göstermek sık sık yararlıdır. Kaynak gizleme bölümünde, uyarının oluşturulduğu yere gizleme için bir gizleme koymanıza izin veren yararlı olur.

 Göstermeme 'nın kaynak kodda veya genel gizleme dosyasında görünüp görünmeyeceğini seçebilirsiniz. Bazı gizlemeleri, genel gizleme dosyasına yerleştirilmelidir. Bu durumda, **kaynak** seçeneğinde seçeneği devre dışı bırakılır.

### <a name="to-suppress-a-warning-by-using-menu-item"></a>Menü öğesini kullanarak bir uyarıyı gizlemek için

1. **Çözümle** menüsünde **Windows** ' u ve ardından **Kod Analizi**' ni seçin.

2. **Kod Analizi** penceresinde, uyarı bastır ' u seçin.

3. Eylemler ' i seçin, sonra **iletileri**göster ' i seçin ve ardından **kaynak** veya **Proje gizleme dosyasında**öğesini seçin.

     Belirli bir uyarı bastırılır ve uyarı, Kod Analizi penceresinde üstü çizili olarak görünür.

> [!NOTE]
> Hedefi olmayan gizlemeleri, genel gizleme dosyasında görünür.
