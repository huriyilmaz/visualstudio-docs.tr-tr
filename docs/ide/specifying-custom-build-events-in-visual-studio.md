---
title: Özel derleme olayları belirtme
description: bir yapı başlamadan veya bittikten sonra Visual Studio komutları otomatik olarak nasıl çalıştırabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- build events, customizing
ms.assetid: 69e935a5-e208-4bcd-865c-3e5f9b047ca8
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 19b974d9e67cb2713299928f3a7e945e9208dcd8cf8c56978a019ed98f88aea7
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121411964"
---
# <a name="specify-custom-build-events-in-visual-studio"></a>Visual Studio özel derleme olayları belirtme

Özel bir yapı olayı belirterek, bir yapı başlamadan veya tamamlanmadan önce komutları otomatik olarak çalıştırabilirsiniz. Örneğin, bir yapı başlamadan önce bir *.bat* dosyası çalıştırabilir veya derleme tamamlandıktan sonra yeni dosyaları bir klasöre kopyalayabilirler. Yapı olayları yalnızca derleme yapı işlemindeki bu noktalara başarıyla ulaşırsa çalışır.

Kullanmakta olduğunuz programlama diliyle ilgili belirli bilgiler için aşağıdaki konulara bakın:

- Visual Basic--[nasıl yapılır: derleme olayları belirtme (Visual Basic)](../ide/how-to-specify-build-events-visual-basic.md).

- C# ve F #--[nasıl yapılır: derleme olayları belirtme (C#)](../ide/how-to-specify-build-events-csharp.md).

- Visual C++--[derleme olaylarını belirtin](/cpp/build/specifying-build-events).

## <a name="syntax"></a>Syntax

Derleme olayları, DOS komutlarıyla aynı sözdizimini izler, ancak daha kolay derleme olayları oluşturmak için makroları kullanabilirsiniz. Kullanılabilir makrolar listesi için bkz. [derleme öncesi olay/oluşturma sonrası olay komut satırı iletişim kutusu](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md).

En iyi sonuçlar için şu biçimlendirme ipuçlarına uyun:

- `call` *.bat* dosyalarını çalıştıran tüm derleme olaylarından önce bir ifade ekleyin.

   Örnek: `call C:\MyFile.bat`

   Örnek: `call C:\MyFile.bat call C:\MyFile2.bat`

- Dosya yollarını tırnak işaretleri içine alın.

   örnek (için [!INCLUDE[win8](../debugger/includes/win8_md.md)] ): "% ProgramFiles (x86)% \ Microsoft sdk \ Windows \v8.0a\bin\netfx 4,0 Tools\gacutil.exe"-ıf "$ (TargetPath)"

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
