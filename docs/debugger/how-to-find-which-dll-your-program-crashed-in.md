---
title: Programınızın hangi DLL 'de kilitlendiğini bulun | Microsoft Docs
description: Uygulamanız kilitlenirse hangi dış DLL 'nin etkin olduğunu belirlemek için modüller penceresini kullanın. Bunu bir sistem DLL 'i veya başka birinin kodu için yapabilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.debug.dll
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, DLL crashes
- Module List dialog box
- errors [debugger], DLL crashes
- Modules window
- debugging [Visual Studio], DLL crashes
- DLLs, load order of
ms.assetid: ecf62568-8b65-4a41-b8a4-e962ff2dfb71
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: d4336c741aac8eded2ce529f5a3fa57dd5abf1d6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122128370"
---
# <a name="how-to-find-which-dll-your-program-crashed-in-c-c-visual-basic-f"></a>nasıl yapılır: programınızın hangi DLL 'de kilitlendiğini bulma (C#, C++, Visual Basic, F #)

 Uygulamanız bir sistem DLL 'SI veya başka birinin kodu çağrısı sırasında kilitlenirse, kilitlenme oluştuğunda hangi DLL 'nin etkin olduğunu bulmanız gerekir. Kendi programınızın dışında bir DLL 'de kilitlenmeyle karşılaşırsanız, bu konumu **modüller** penceresini kullanarak belirleyebilirsiniz.

### <a name="to-find-where-a-crash-occurred-using-the-modules-window"></a>Modüller penceresini kullanarak bir kilitlenmenin nerede oluştuğunu bulmak için

1. Çökmenin gerçekleştiği adresi aklınızda edin.

    Adres hata iletisinde gösterilmiyorsa, DLL 'yi tanımlamak için alternatif yöntemler kullanmanız gerekebilir. Bir sistem DLL 'inin şüpheli olması halinde, hata ayıklama sırasında Microsoft sembol sunucularından [sembolleri](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) yükleyebilirsiniz. Aksi takdirde, bunun yerine yığın bilgileriyle [bir döküm dosyası oluşturmanız](../debugger/using-dump-files.md) gerekebilir. Döküm dosyaları oluşturmak için çeşitli [Araçlar](https://blogs.msdn.microsoft.com/andrehal/2009/12/31/what-is-a-dump-and-how-do-i-create-one/) mevcuttur.

2. **hata ayıkla** menüsünde, **Windows** öğesini seçin ve **modüller**' e tıklayın.

3. **Modüller** penceresinde **Adres** sütununu bulun. Bunu görmek için kaydırma çubuğunu kullanmanız gerekebilir.

4. Dll 'Leri adrese göre sıralamak için sütunun en üstündeki **Adres** düğmesine tıklayın.

5. Adres aralığı kilitlenme konumunu içeren DLL 'yi bulmak için sıralanmış listeyi tarayın.

6. DLL adını ve yolunu görmek için **ad** ve **yol** sütunlarına bakın.

## <a name="see-also"></a>Ayrıca bkz.
- [DLL Projelerinde Hata Ayıklama](../debugger/debugging-dll-projects.md)
- [Nasıl Yapılır: Modüller Penceresini Kullanma](../debugger/how-to-use-the-modules-window.md)