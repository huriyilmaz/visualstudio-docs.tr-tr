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
ms.openlocfilehash: 169401462589b12c9d0d337d442c4288bf4e16ad
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126724883"
---
# <a name="create-minidumps-for-a-visual-studio-process-with-all-call-stacks"></a>Tüm çağrı yığınları ile bir Visual Studio için minidumps oluşturma

Bazı durumlarda Microsoft, tüm çağrı yığınları için bilgi Visual Studio çalışan bir işlem için bir minidump sorabilir. Bu bilgileri toplamak için şu adımları gerçekleştirin:

## <a name="create-the-minidump-file"></a>Minidump dosyasını oluşturma

1. Yeni bir örnek Visual Studio.
1. Ana menüden İşleme **Eklemede Hata**  >  **Ayıkla'ya tıklayın.**
1. İlgili Yönetilen ve **Yerel onay** **kutularını işaretleyin** ve Ekle'ye **basın.**

   ![İşleme ekle](../ide/media/attach-to-process.png)

1. Çalışan işlemler Visual Studio eklemek istediğiniz diğer örnek örneği seçin.
1. Ana menüden Hata Ayıkla **Tüm Hata**  >  **Ayıklama'ya tıklayın.**
1. Ana menüden Döküm dökümlerini Farklı **Kaydet hata**  >  **ayıkla'ya tıklayın.**

## <a name="get-the-call-stacks-from-the-minidump"></a>Minidump'tan çağrı yığınlarını al

1. Döküm dosyasını Visual Studio.
1. Araçlar Seçenekler  >  **Sembollerde**  >  **Hata Ayıklama'ya** gidin ve Sembol dosyası  >   **(.pdb)**  konumlarında Microsoft Sembol Sunucularının işaretli olduğundan emin olun.
1. Komut penceresini **açın** (**Diğer**  >  **Windows**  >  **Komut Penceresini Görüntüle**)
1. '~*k' yazın. Pencerede tüm iş parçacıklarının çağrı yığınları görüntülenir.
1. Komut Penceresindeki tüm metni kopyalayın ve bir metin dosyasına kaydedin.
1. Txt dosyasını hataya iliştirin.
