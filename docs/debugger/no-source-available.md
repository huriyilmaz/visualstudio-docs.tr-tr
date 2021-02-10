---
title: Kullanılabilir kaynak yok | Microsoft Docs
description: Projenizde görüntülemek istediğiniz kod için kaynak kodu yoksa ne yapabileceğinizi öğrenin.
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
ms.workload:
- multiple
ms.openlocfilehash: e9993c4482d20393a3ca46d9afcd0a8ec1b13f65
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942041"
---
# <a name="no-source-available"></a>Kullanılabilir Kaynak Yok
Projeniz, görüntülemeye çalıştığınız kodun kaynak kodunu içermiyor. Bunun nedeni, **çağrı yığını penceresinde** veya **iş parçacıkları penceresinde** kaynak kodu olmayan bir modüle çift tıklanıdır. Hata ayıklamaya devam edebilir, ancak kesme noktaları ayarlamak ve bu konumda diğer eylemleri gerçekleştirmek için kaynak pencereyi kullanamazsınız. Bir kesme noktası ayarlamanız gerekiyorsa, bunun yerine **ayrıştırma penceresini** kullanın.

 Çözüm özelliği sayfalarında, hata ayıklayıcının kaynak dosyalarını aradığı dizinleri değiştirebilir ve hata ayıklayıcıya seçili kaynak dosyaları yoksaymasını söyleyebilirsiniz. Bkz. [hata ayıklama kaynak dosyaları, ortak özellikler, çözüm Özellik sayfaları Iletişim kutusu](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md).

 **Kaynak kodunu bulmak Için gidin** Kaynak kodunu bulmak için gözatabileceğiniz bir iletişim kutusu açmak için bu bağlantıya tıklayın.

 **Ayrıştırılmış kodu göster** **Ayrıştırma penceresini** başlatır.

 **Eksik kaynak dosyaları Için her zaman ayrıştırılmış kodu göster** Kaynak kullanılabilir olmadığında **ayrıştırma penceresini** otomatik olarak göstermek için bu seçeneği belirleyin. Bu ayar ayrıca **Seçenekler** iletişim kutusunda, **hata ayıklama** kategorisinde, **genel** sayfasında, **Kaynak kullanılamıyorsa ayrıştırılmış derlemeyi göster**' i seçerek veya temizleyerek da değiştirilebilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak dosyalarında hata ayıkla, ortak özellikler, çözüm Özellik sayfaları Iletişim kutusu](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md)
- [Simge (.pdb) ve Kaynak Dosyaları Belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [SOS.dll (SOS hata ayıklama uzantısı)](/dotnet/framework/tools/sos-dll-sos-debugging-extension)