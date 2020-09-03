---
title: Kodlamalar ve satır sonları | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.Encoding
helpviewer_keywords:
- line breaks
- encoding
- Visual Studio, encoding
- editors, line breaks
- line break characters
- Visual Studio, line break characters
ms.assetid: 8f9b3ffc-7b8d-44f4-87cb-dc29105be12d
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2e1b13cc101ea4d7609633fd9c11bf87946d7b7d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665733"
---
# <a name="encodings-and-line-breaks"></a>Kodlamalar ve Satır Sonları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 'da istediğiniz satır sonu karakterlerinin türünü öğrenmek için **Dosya/Gelişmiş kaydetme seçenekleri** ayarlarını kullanabilirsiniz. Aynı ayarlarla bir dosyanın kodlamasını de değiştirebilirsiniz.

> [!NOTE]
> Belirli türde geliştirme ayarlarına sahipseniz (Visual Basic, F #, Web geliştirme) menüde **Gelişmiş Kaydet seçeneklerini** göremeyebilirsiniz. Ayarlarınızı değiştirmek için (örneğin, genel), **Araçlar/içeri ve dışarı aktarma ayarları**' nı açın. Daha fazla bilgi için bkz. [Visual Studio 'Da geliştirme ayarlarını özelleştirme](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

 Visual Studio 'da aşağıdaki karakterler satır sonları olarak yorumlanır:

- CRLF: satır başı + satır besleme, Unicode karakterler 000D + 000A

- LF: satır besleme, Unicode karakter 000A

- NEL: sonraki satır, Unicode karakter 0085

- LS: satır ayırıcı, Unicode karakter 2028

- PS: paragraf ayırıcı, Unicode karakter 2029

  Diğer uygulamalardan kopyalanmış olan metin özgün kodlamayı ve satır sonu karakterlerini tutar. Örneğin, Not defteri 'nden metin kopyaladığınızda ve Visual Studio 'daki bir metin dosyasına yapıştırdığınızda, metin Notepad 'de bulunan aynı ayarlara sahiptir.

  Farklı satır sonu karakterleri olan bir dosyayı açtığınızda tutarsız çizgi kesme karakterlerinin normalleştirilip normalleştirilmeyeceğini ve ne tür satır sonlarını seçeceğini soran bir iletişim kutusu görebilirsiniz.
