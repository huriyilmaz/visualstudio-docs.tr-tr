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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f33dd9b19297811597be406337d70392904e6e44
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75596396"
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

## <a name="see-also"></a>Ayrıca bkz.

- [Çözümler ve projeler](../../ide/solutions-and-projects-in-visual-studio.md)
