---
title: Tüm çağrı yığınları ile minidumps oluşturma
description: Tüm çağrı yığınları için bilgi içeren bir Visual Studio minidumps oluşturma hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 06/27/2019
ms.topic: how-to
helpviewer_keywords:
- minidumps for Visual Studio issues"
author: corob-msft
ms.author: corob
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.description: Collect minidumps to send to Microsoft for help with troubleshooting issues with Visual Studio
ms.openlocfilehash: 0f25c87933ecabee224cdc07ffc120a9b4908b18748528852ac07d64bc496067
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121371715"
---
# <a name="create-minidumps-for-a-visual-studio-process-with-all-call-stacks"></a>Tüm çağrı yığınları ile Visual Studio bir işlem için minidumps oluşturma

Bazı durumlarda Microsoft, tüm çağrı yığınları için bilgi Visual Studio çalışan bir işlem için bir minidump sorabilir. Bu bilgileri toplamak için şu adımları gerçekleştirin:

## <a name="create-the-minidump-file"></a>Minidump dosyasını oluşturma

1. Yeni bir örnek Visual Studio.
1. Ana menüden İşleme **Eklemede Hata**  >  **Ayıkla'ya tıklayın.**
1. İlgili Yönetilen ve **Yerel onay** **kutularını işaretleyin** ve Ekle'ye **basın.**

   ![İşleme ekle](../ide/media/attach-to-process.png)

1. Çalışan işlemler Visual Studio eklemek için diğer örnek örnek seçin.
1. Ana menüden Hata Ayıkla **Tüm Hataları**  >  **Ayıkla'ya tıklayın.**
1. Ana menüden Döküm dökümlerini Farklı **Kaydet hata**  >  **ayıkla'ya tıklayın.**

## <a name="get-the-call-stacks-from-the-minidump"></a>Minidump'tan çağrı yığınlarını al

1. Döküm dosyasını Visual Studio.
1. Araçlar Seçenekler  >  **Sembollerde**  >  **Hata Ayıklama'ya** gidin ve Sembol dosyası  >   **(.pdb)**  konumlarında Microsoft Sembol Sunucularının işaretli olduğundan emin olun.
1. Komut penceresini **açın** (**Diğer Komut**  >  **Windows**  >  **Penceresini Görüntüle**)
1. '~*k' yazın. Pencerede tüm iş parçacıklarının çağrı yığınları görüntülenir.
1. Komut Penceresindeki tüm metni kopyalayın ve bir metin dosyasına kaydedin.
1. Txt dosyasını hataya iliştirin.
