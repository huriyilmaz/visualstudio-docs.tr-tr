---
title: Tüm çağrı yığınları ile mini döküm oluşturma
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
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/15/2020
ms.locfileid: "77271192"
---
# <a name="create-minidumps-for-a-visual-studio-process-with-all-call-stacks"></a>Tüm çağrı yığınlarıyla Visual Studio işlemi için mini döküm oluşturma

Bazı durumlarda Microsoft, çalışan bir Visual Studio işleminin tüm çağrı yığınları hakkında bilgi içeren bir mini döküm isteyebilir. Bu bilgileri toplamak için şu adımları uygulayın:

## <a name="create-the-minidump-file"></a>Mini döküm dosyası oluşturma

1. Visual Studio 'nun yeni bir örneğini başlatın.
1. Ana menüden **hata ayıkla** > **İşleme İliştir**' i seçin.
1. İlgili **yönetilen** ve **Yerel** onay kutularını işaretleyin ve **Ekle**'ye basın.

   ![İşleme İliştir](../ide/media/attach-to-process.png)

1. Çalışan işlemlerin listesinden iliştirilecek diğer Visual Studio örneğini seçin.
1. Ana menüden **hata ayıkla** > **Tümünü kes**' i seçin.
1. Ana menüden **hata ayıkla** > **dökümü farklı kaydet**' i seçin.

## <a name="get-the-call-stacks-from-the-minidump"></a>Mini döküm dosyasından çağrı yığınlarını al

1. Döküm dosyasını Visual Studio 'da açın.
1. **Araçlar** > **Seçenekler** ' e gidin > **sembolleri** **hata ayıklama** > ve **Microsoft sembol sunucularının** **sembol dosyası (. pdb) konumlarında**işaretli olduğundan emin olun.
1. **Komut** penceresini açın ( **diğer Windows** > **komut penceresini** > **görüntüleyin** )
1. ' ~ * K ' yazın. Pencerede tüm iş parçacıklarının çağrı yığınları görüntülenir.
1. Komut penceresinden tüm metni kopyalayın ve bir metin dosyasına kaydedin.
1. Txt dosyasını hataya iliştirin.
