---
title: Kullanılabilir Kaynak yok | Microsoft Docs
description: Projeniz, görüntülemek istediğiniz kod için kaynak koduna sahip değilken neler yaplarınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.nosource
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- No Source Code Available for the Current Location dialog box
ms.assetid: ed0732bc-4b8c-490f-adb1-af06869a2a6b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 1ef2f84547a99906caf07ebce0d41f7b7a9a5655
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122030704"
---
# <a name="no-source-available"></a>Kullanılabilir Kaynak Yok
Projeniz, görüntülemeye çalıştığınız kodun kaynak kodunu içermez. Her zamanki neden Çağrı Yığını Penceresi veya İş Parçacıkları Penceresinde kaynak kodu olmayan bir **modüle çift** **tıklamaktır.** Hata ayıklamaya devam edersiniz, ancak kesme noktaları ayarlamak ve bu konumda başka eylemler gerçekleştirmek için kaynak pencereyi kullanılamaz. Bir kesme noktası ayarlamaya ihtiyacınız varsa, bunun **yerine Disassembly Window kullanın.**

 Çözüm Özellik Sayfaları'da, hata ayıklayıcının kaynak dosyalarını bulmak için bulunduğu dizinleri değiştirebilir ve hata ayıklayıcıya seçili kaynak dosyaları yoksaymalarını söylersiniz. Bkz. [Kaynak Dosyalarda Hata Ayıklama, Ortak Özellikler, Çözüm Özelliği Sayfaları İletişim Kutusu.](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md)

 **Kaynak kodunu bulmak için göz atma** Kaynak kodu bulmak için göz atabilirsiniz bir iletişim kutusu açmak için bu bağlantıya tıklayın.

 **Disassembly Gösterme** **Disassembly Penceresini açar.**

 **Eksik kaynak dosyalar için her zaman disassembly göster** Kaynak kullanılabilir durumda değilken **Otomatik Olarak Ayır Penceresini görüntülemek** için bu seçeneği belirleyin. Bu ayar Seçenekler iletişim  **kutusunda,** Hata ayıklama kategorisi, **Genel** sayfasında kaynak kullanılamıyorsa Farklı göster'i seçerek veya temizerek **de değiştirilebilir.**

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Dosyalarda Hata Ayıklama, Ortak Özellikler, Çözüm Özellik Sayfaları İletişim Kutusu](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md)
- [Simge (.pdb) ve Kaynak Dosyaları Belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [SOS.dll (SOS Hata Ayıklama Uzantısı)](/dotnet/framework/tools/sos-dll-sos-debugging-extension)