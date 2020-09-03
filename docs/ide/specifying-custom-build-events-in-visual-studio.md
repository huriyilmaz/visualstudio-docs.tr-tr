---
title: Özel derleme olayları belirtme
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- build events, customizing
ms.assetid: 69e935a5-e208-4bcd-865c-3e5f9b047ca8
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fda60ffb97ecb44bd4a881cb42e4d9199cc958b8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "76115334"
---
# <a name="specify-custom-build-events-in-visual-studio"></a>Visual Studio 'da özel derleme olayları belirtme

Özel bir yapı olayı belirterek, bir yapı başlamadan veya tamamlanmadan önce komutları otomatik olarak çalıştırabilirsiniz. Örneğin, bir yapı başlamadan önce bir *. bat* dosyası çalıştırabilir veya derleme tamamlandıktan sonra yeni dosyaları bir klasöre kopyalayabilirler. Yapı olayları yalnızca derleme yapı işlemindeki bu noktalara başarıyla ulaşırsa çalışır.

Kullanmakta olduğunuz programlama diliyle ilgili belirli bilgiler için aşağıdaki konulara bakın:

- Visual Basic--[nasıl yapılır: derleme olayları belirtme (Visual Basic)](../ide/how-to-specify-build-events-visual-basic.md).

- C# ve F #--[nasıl yapılır: derleme olayları belirtme (C#)](../ide/how-to-specify-build-events-csharp.md).

- Visual C++--[derleme olaylarını belirtin](/cpp/build/specifying-build-events).

## <a name="syntax"></a>Syntax

Derleme olayları, DOS komutlarıyla aynı sözdizimini izler, ancak daha kolay derleme olayları oluşturmak için makroları kullanabilirsiniz. Kullanılabilir makrolar listesi için bkz. [derleme öncesi olay/oluşturma sonrası olay komut satırı iletişim kutusu](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md).

En iyi sonuçlar için şu biçimlendirme ipuçlarına uyun:

- `call` *. Bat* dosyalarını çalıştıran tüm derleme olaylarından önce bir ifade ekleyin.

   Örnek: `call C:\MyFile.bat`

   Örnek: `call C:\MyFile.bat call C:\MyFile2.bat`

- Dosya yollarını tırnak işaretleri içine alın.

   Örnek (için [!INCLUDE[win8](../debugger/includes/win8_md.md)] ): "% ProgramFiles (x86)% \ Microsoft SDKs\Windows\v8.0A\Bin\NETFX 4,0 Tools\gacutil.exe"-If "$ (TargetPath)"

- Satır sonlarını kullanarak birden çok komutu ayırın.

- Gerektiğinde joker karakterleri ekleyin.

   Örnek: `for %I in (*.txt *.doc *.html) do copy %I c:\` *mydirectory*`\`

  > [!NOTE]
  > `%I` Yukarıdaki kodda `%%I` toplu betiklerin olması gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [Derleme ve oluşturma](../ide/compiling-and-building-in-visual-studio.md)
- [Oluşturma öncesi olay/oluşturma sonrası olay komut satırı iletişim kutusu](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)
- [MSBuild özel karakterleri](../msbuild/msbuild-special-characters.md)
- [İzlenecek yol: Uygulama oluşturma](../ide/walkthrough-building-an-application.md)
