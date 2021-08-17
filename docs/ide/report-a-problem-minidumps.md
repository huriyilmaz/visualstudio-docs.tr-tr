---
title: Tüm çağrı yığınları ile mini döküm oluşturma
description: tüm çağrı yığınları için bilgi içeren Visual Studio bir işlem için mini dökümler oluşturmayı öğrenin.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122048589"
---
# <a name="create-minidumps-for-a-visual-studio-process-with-all-call-stacks"></a>tüm çağrı yığınlarıyla bir Visual Studio işlemi için mini dökümler oluşturma

bazı durumlarda Microsoft, çalışan bir Visual Studio işleminin tüm çağrı yığınlarıyla ilgili bilgilerle ilgili bir mini döküm isteyebilir. Bu bilgileri toplamak için şu adımları uygulayın:

## <a name="create-the-minidump-file"></a>Mini döküm dosyası oluşturma

1. Visual Studio yeni bir örneğini başlatın.
1. Ana menüden,   >  **işleme Ekle** Hata Ayıkla ' yı seçin.
1. İlgili **yönetilen** ve **Yerel** onay kutularını işaretleyin ve **Ekle**'ye basın.

   ![İşleme ekle](../ide/media/attach-to-process.png)

1. çalışan işlemlerin listesinden iliştirilecek diğer Visual Studio örneğini seçin.
1. Ana menüden **Hata Ayıkla**  >  **Tümünü kes**' i seçin.
1. Ana menüden,   >  **dökümü farklı kaydet kayıt** Ayıkla ' yı seçin.

## <a name="get-the-call-stacks-from-the-minidump"></a>Mini döküm dosyasından çağrı yığınlarını al

1. Döküm dosyasını Visual Studio ' de açın.
1. **Araçlar**  >  **Seçenekler**  >  **hata ayıklama**  >  **simgeleri** ' ne gidin ve **sembol dosyası (. pdb) konumlarında** **Microsoft sembol sunucularının** işaretli olduğundan emin olun.
1. **komut** penceresini açın (  >  **diğer Windows**  >  **komut penceresini** görüntüle)
1. ' ~ * K ' yazın. Pencerede tüm iş parçacıklarının çağrı yığınları görüntülenir.
1. Komut penceresinden tüm metni kopyalayın ve bir metin dosyasına kaydedin.
1. Txt dosyasını hataya iliştirin.
