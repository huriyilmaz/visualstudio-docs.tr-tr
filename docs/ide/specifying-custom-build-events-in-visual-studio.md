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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76115334"
---
# <a name="specify-custom-build-events-in-visual-studio"></a>Visual Studio'da özel yapı olaylarını belirtin

Özel bir yapı olayı belirterek, komutları oluşturma başlamadan önce veya bittikten sonra otomatik olarak çalıştırabilirsiniz. Örneğin, yapı başlamadan önce bir *.bat* dosyasını çalıştırabilir veya yapı tamamlandıktan sonra yeni dosyaları bir klasöre kopyalayabilirsiniz. Yapı olayları yalnızca yapı işleminde bu noktalara başarıyla ulaşırsa çalışır.

Kullanmakta olduğunuz programlama dili hakkında özel bilgiler için aşağıdaki konulara bakın:

- Visual Basic-[Nasıl Yapılır: Yapı olaylarını belirtin (Visual Basic)](../ide/how-to-specify-build-events-visual-basic.md).

- C# ve F#--[Nasıl yapılır: Yapı olayları (C#) belirtin.](../ide/how-to-specify-build-events-csharp.md)

- Visual C++--[Yapı olayları belirtin.](/cpp/build/specifying-build-events)

## <a name="syntax"></a>Sözdizimi

Yapı olayları DOS komutları ile aynı sözdizimini izler, ancak yapı olayları oluşturmak için makroları daha kolay kullanabilirsiniz. Kullanılabilir makroların listesi için, [Önceden Yapı Olay/Post-build Olay komut satırı iletişim kutusuna](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)bakın.

En iyi sonuçlar için şu biçimlendirme ipuçlarını izleyin:

- `call` *.bat* dosyalarını çalıştıran tüm yapı olayları önce bir deyim ekleyin.

   Örnek: `call C:\MyFile.bat`

   Örnek: `call C:\MyFile.bat call C:\MyFile2.bat`

- Dosya yollarını tırnak işaretlerine ekin.

   Örnek (örneğin): [!INCLUDE[win8](../debugger/includes/win8_md.md)]"%ProgramFiles(x86)%\Microsoft SDKs\Windows\v8.0A\Bin\NETFX 4.0 Tools\gacutil.exe" -if "$(TargetPath)"

- Satır sonları kullanarak birden çok komutu ayırın.

- Gerektiğinde joker karakterleri ekleyin.

   Örnek: `for %I in (*.txt *.doc *.html) do copy %I c:\` *mydirectory*`\`

  > [!NOTE]
  > `%I`yukarıdaki kodda toplu `%%I` komut dosyaları olmalıdır.

## <a name="see-also"></a>Ayrıca bkz.

- [Derleme ve oluşturma](../ide/compiling-and-building-in-visual-studio.md)
- [Önceden Oluşturma Olay/Post-build Olay komut satırı iletişim kutusu](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)
- [MSBuild özel karakterleri](../msbuild/msbuild-special-characters.md)
- [İzlenecek yol: Uygulama oluşturma](../ide/walkthrough-building-an-application.md)
