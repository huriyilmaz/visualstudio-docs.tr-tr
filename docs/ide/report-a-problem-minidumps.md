---
title: Tüm çağrı yığınları ile mini döküm oluşturma
description: Tüm çağrı yığınları için bilgi içeren bir Visual Studio işlemi için mini döküm oluşturmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 06/27/2019
ms.topic: how-to
helpviewer_keywords:
- minidumps for Visual Studio issues"
author: corob-msft
ms.author: corob
manager: jmartens
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.description: Collect minidumps to send to Microsoft for help with troubleshooting issues with Visual Studio
ms.openlocfilehash: 44ab0873580c7c541fc5e7fdde56cc1780929b75
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970783"
---
# <a name="create-minidumps-for-a-visual-studio-process-with-all-call-stacks"></a>Tüm çağrı yığınlarıyla Visual Studio işlemi için mini döküm oluşturma

Bazı durumlarda Microsoft, çalışan bir Visual Studio işleminin tüm çağrı yığınları hakkında bilgi içeren bir mini döküm isteyebilir. Bu bilgileri toplamak için şu adımları uygulayın:

## <a name="create-the-minidump-file"></a>Mini döküm dosyası oluşturma

1. Visual Studio 'nun yeni bir örneğini başlatın.
1. Ana menüden,   >  **işleme Ekle** Hata Ayıkla ' yı seçin.
1. İlgili **yönetilen** ve **Yerel** onay kutularını işaretleyin ve **Ekle**'ye basın.

   ![İşleme ekle](../ide/media/attach-to-process.png)

1. Çalışan işlemlerin listesinden iliştirilecek diğer Visual Studio örneğini seçin.
1. Ana menüden **Hata Ayıkla**  >  **Tümünü kes**' i seçin.
1. Ana menüden,   >  **dökümü farklı kaydet kayıt** Ayıkla ' yı seçin.

## <a name="get-the-call-stacks-from-the-minidump"></a>Mini döküm dosyasından çağrı yığınlarını al

1. Döküm dosyasını Visual Studio 'da açın.
1. **Araçlar**  >  **Seçenekler**  >  **hata ayıklama**  >  **simgeleri** ' ne gidin ve **sembol dosyası (. pdb) konumlarında** **Microsoft sembol sunucularının** işaretli olduğundan emin olun.
1. **Komut** penceresini açın (  >  **diğer Windows**  >  **komut penceresini** görüntüle)
1. ' ~ * K ' yazın. Pencerede tüm iş parçacıklarının çağrı yığınları görüntülenir.
1. Komut penceresinden tüm metni kopyalayın ve bir metin dosyasına kaydedin.
1. Txt dosyasını hataya iliştirin.
