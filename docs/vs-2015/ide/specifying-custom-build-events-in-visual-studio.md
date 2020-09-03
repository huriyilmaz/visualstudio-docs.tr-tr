---
title: Özel Derleme Olayları Belirtme
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- build events, customizing
ms.assetid: 69e935a5-e208-4bcd-865c-3e5f9b047ca8
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fabbd4dc42ac4f66c7f53b639c6e7ed1f432878c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667123"
---
# <a name="specifying-custom-build-events-in-visual-studio"></a>Visual Studio'da Özel Yapı Olayları Belirtme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Özel bir yapı olayı belirterek, bir yapı başlamadan veya tamamlanmadan önce komutları otomatik olarak çalıştırabilirsiniz. Örneğin, bir yapı başlamadan önce bir. bat dosyası çalıştırabilir veya derleme tamamlandıktan sonra yeni dosyaları bir klasöre kopyalayabilirler. Yapı olayları yalnızca derleme yapı işlemindeki bu noktalara başarıyla ulaşırsa çalışır.

 Kullanmakta olduğunuz programlama diliyle ilgili belirli bilgiler için aşağıdaki konulara bakın:

- Visual Basic--[nasıl yapılır: derleme olayları belirtme (Visual Basic)](../ide/how-to-specify-build-events-visual-basic.md).

- Visual C# ve F #--[nasıl yapılır: derleme olayları belirtme (C#)](../ide/how-to-specify-build-events-csharp.md).

- Visual C++--[derleme olayları belirtme](https://msdn.microsoft.com/library/788a6c18-2dbe-4a49-8cd6-86c1ad7a95cc).

## <a name="syntax"></a>Syntax
 Derleme olayları, DOS komutlarıyla aynı sözdizimini izler, ancak daha kolay derleme olayları oluşturmak için makroları kullanabilirsiniz. Kullanılabilir makrolar listesi için bkz. [derleme öncesi olay/oluşturma sonrası olay komut satırı Iletişim kutusu](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md).

 En iyi sonuçlar için şu biçimlendirme ipuçlarına uyun:

- `call`. Bat dosyalarını çalıştıran tüm derleme olaylarından önce bir ifade ekleyin.

     Örnek: `call C:\MyFile.bat`

     Örnek: `call C:\MyFile.bat call C:\MyFile2.bat`

- Dosya yollarını tırnak işaretleri içine alın.

     Örnek (için [!INCLUDE[win8](../includes/win8-md.md)] ): "% ProgramFiles (x86)% \ Microsoft SDKs\Windows\v8.0A\Bin\NETFX 4,0 Tools\gacutil.exe"-If "$ (TargetPath)"

- Satır sonlarını kullanarak birden çok komutu ayırın.

- Gerektiğinde joker karakterleri ekleyin.

     Örnek: `for %I in (*.txt *.doc *.html) do copy %I c:\` *mydirectory*`\`

    > [!NOTE]
    > `%I` Yukarıdaki kodda `%%I` toplu betiklerin olması gerekir.

## <a name="see-also"></a>Ayrıca Bkz.
 [Compiling and Building](../ide/compiling-and-building-in-visual-studio.md) [Derleme öncesi olay oluşturma ve derleme sonrası olay komut satırı Iletişim kutusu](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md) [MSBuild özel karakterler](../msbuild/msbuild-special-characters.md) [izlenecek yol: uygulama oluşturma](../ide/walkthrough-building-an-application.md)
