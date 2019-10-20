---
title: Visual Basic Varsayılanları, Projeler, Seçenekler İletişim Kutusu
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.VBDefaults
helpviewer_keywords:
- Option Explicit statement, setting in the IDE
- Option Compare statement, setting in the IDE
- Option Strict statement, setting in the IDE
ms.assetid: 2465cd9d-18b6-4c4a-b1ea-86dbab23fc79
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 64641ebf47e5a5c91b7e20f1ddafe9490649ec9a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72622393"
---
# <a name="visual-basic-defaults-projects-options-dialog-box"></a>Visual Basic Varsayılanları, Projeler, Seçenekler İletişim Kutusu
Visual Basic proje seçenekleri için varsayılan ayarları belirtir. Yeni bir proje oluşturulduğunda, belirtilen seçenek deyimleri kod düzenleyicisinde proje başlığına eklenecektir. Seçenekler tüm Visual Basic projelerine uygulanır.

Bu iletişim kutusuna erişmek için, **Araçlar** menüsünde **Seçenekler**' e tıklayın, **Projeler ve çözümler** klasörünü genişletin ve ardından **vb Varsayılanları**' na tıklayın.

 **Seçenek açık**

Doğrudan değişken bildirimlerinin gerekli olduğu şekilde derleyici varsayılanını ayarlar. Varsayılan olarak, **explicit seçeneği** **Açık olarak ayarlanır.** Daha fazla bilgi için bkz. [/OptionExplicit](/dotnet/visual-basic/reference/command-line-compiler/optionexplicit).

 **Option Strict**

Açık daraltma dönüştürmelerini zorunlu ve geç bağlamaya izin verilmediğinden, derleyici varsayılanını varsayılan olarak ayarlar. Varsayılan olarak, **Strict seçeneği** **off**olarak ayarlanır. Daha fazla bilgi için bkz. [/OptionStrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict).

 **Option Compare**

Dize karşılaştırmaları için derleyici varsayılanını ayarlar: ikili (büyük/küçük harfe duyarlı) veya metin (büyük/küçük harfe duyarsız.) Varsayılan olarak, **Option Compare** **binary**olarak ayarlanır. Daha fazla bilgi için bkz. [/OptionCompare](/dotnet/visual-basic/reference/command-line-compiler/optioncompare).

 **Seçenek çıkarımı**

Yerel tür çıkarımı için varsayılan derleyicisini ayarlar. Varsayılan olarak, **seçenek çıkarımı** yeni oluşturulan projeler için **Açık** olarak ayarlanır ve Visual Basic önceki sürümlerinde oluşturulan geçirilmiş projeler için **devre dışı bırakır** . Daha fazla bilgi için bkz. [/optionfer](/dotnet/visual-basic/reference/command-line-compiler/optioninfer).

## <a name="see-also"></a>Ayrıca Bkz.

- [Çözümler ve Projeler](../../ide/solutions-and-projects-in-visual-studio.md)