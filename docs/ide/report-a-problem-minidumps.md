---
title: Tüm çağrı yığınlarıyla minidökümler oluşturma
ms.date: 06/27/2019
ms.topic: conceptual
helpviewer_keywords:
- minidumps for Visual Studio issues"
author: corob-msft
ms.author: corob
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.description: Collect minidumps to send to Microsoft for help with troubleshooting issues with Visual Studio
ms.openlocfilehash: 7b3be91e5d0d2e1f14724dd647670fc4885bcd4d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77271192"
---
# <a name="create-minidumps-for-a-visual-studio-process-with-all-call-stacks"></a>Tüm çağrı yığınlarıyla Visual Studio işlemi için minidökümler oluşturun

Bazı durumlarda, Microsoft tüm arama yığınları için bilgi ile çalışan bir Visual Studio işleminin bir minidump isteyebilir. Bu bilgileri toplamak için şu adımları gerçekleştirin:

## <a name="create-the-minidump-file"></a>Minidump dosyasını oluşturma

1. Visual Studio'nun yeni bir örneğini başlatın.
1. Ana menüden **Hata Ayıklama** > **İşleme Ekle'yi**seçin.
1. İlgili **Yönetilen** ve **Yerel** onay kutularını kontrol edin ve **Ekle'ye**basın.

   ![İşleme ekle](../ide/media/attach-to-process.png)

1. Çalışan işlemler listesinden eklemek için diğer Visual Studio örneğini seçin.
1. Ana menüden **Hata Ayıklama** > **Tümlerini Kır'ı**seçin.
1. Ana menüden **Hata Ayıklama** > **Dökümü'nü**seçin.

## <a name="get-the-call-stacks-from-the-minidump"></a>Arama yığınlarını minidumptan alın

1. Visual Studio'da döküm dosyasını açın.
1. **Araçlar** > **Seçenekleri** > **Hata Ayıklama** > **Sembolleri'ne** gidin ve Microsoft Symbol **Sunucular'ın** Simge dosyası **(.pdb) konumlarında**işaretli olduğundan emin olun.
1. **Komut** penceresini aç (**Diğer Windows** > **Komut Penceresini****Görüntüle** > )
1. '~*k' yazın. Pencere, tüm iş parçacıklarının çağrı yığınlarını görüntüler.
1. Komut Penceresi'nden tüm metni kopyalayın ve bir metin dosyasına kaydedin.
1. TXT dosyasını hataya takın.
