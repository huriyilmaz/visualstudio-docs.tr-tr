---
title: Kod Parçacıkları İçin En İyi Uygulamalar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- code snippets, best practices
- code snippets, security
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 08add20b59e3e14897d1870aa45fd6cce8698d96
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591716"
---
# <a name="best-practices-for-using-code-snippets"></a>Kod parçacıklarını kullanmak için en iyi uygulamalar

Kod parçacığındaki kod, bir şey yapmanın yalnızca en temel yolunu gösterir. Çoğu uygulama için kodun uygulamaya uyacak şekilde değiştirilmesi gerekir.

## <a name="handling-exceptions"></a>Özel durum işleme

Genellikle, kod parçacığı deneyin ... Catch blokları yakalamak ve tüm özel durumlar yeniden atmak. Bu projeniz için doğru seçim olmayabilir. Her özel durum için, yanıt vermek için çeşitli yollar vardır. Örnekler için [bkz: Try/catch (C#)](/dotnet/csharp/programming-guide/exceptions/how-to-handle-an-exception-using-try-catch) ve [Try... Yakalamak... Son olarak deyimi (Visual Basic)](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement).

## <a name="file-locations"></a>Dosya konumları

Dosya konumlarını uygulamanız için uyarlarken aşağıdakileri düşünmelisiniz:

- Erişilebilir bir konum bulma. Kullanıcılar bilgisayarın *Program Dosyaları* klasörüne erişemeyebilir, bu nedenle dosyaları uygulama dosyalarıyla depolamak çalışmayabilir.

- Güvenli bir yer bulmak. *(C:\\*) kök klasöründe dosya depolama güvenli değildir. Uygulama verileri için *Uygulama Verileri* klasörünü öneririz. Tek tek kullanıcı verileri için uygulama, *Belgeler* klasöründeki her kullanıcı için bir dosya oluşturabilir.

- Geçerli bir dosya adı kullanma. Geçersiz dosya <xref:System.Windows.Forms.OpenFileDialog> adları <xref:System.Windows.Forms.SaveFileDialog> olasılığını azaltmak için ve denetimleri kullanabilirsiniz. Kullanıcının bir dosyayı seçtiği zaman ile kodunuzu işleme zamanı arasında dosyanın silinebileceğini unutmayın. Ayrıca, kullanıcının dosyaya yazma izinleri olmayabilir.

## <a name="security"></a>Güvenlik

Bir parçacığın ne kadar güvenli olduğu, kaynak kodunda nerede kullanıldığına ve kodda olduğunda nasıl değiştirildiğine bağlıdır. Aşağıdaki liste, dikkate alınması gereken alanlardan birkaçını içerir.

- Dosya ve veritabanı erişimi

- Kod erişim güvenliği

- Kaynakları koruma (olay günlükleri, kayıt defteri gibi)

- Sırları depolama

- Girişleri doğrulama

- Komut dosyası teknolojilerine veri aktarma

Daha fazla bilgi için [bkz.](../ide/securing-applications.md)

## <a name="downloaded-code-snippets"></a>İndirilen kod parçacıkları

Visual Studio tarafından yüklenen IntelliSense kod parçacıkları kendi içinde bir güvenlik tehlikesi değildir. Ancak, bunlar uygulamanızda güvenlik riskleri oluşturabilir. Internet'ten indirilen parçacıklar, indirilen diğer içerikler gibi son derece dikkatli davranılmalıdır.

- Parçacıkları yalnızca güvendiğiniz sitelerden indirin ve güncel virüs yazılımlarını kullanın.

- Notepad'de veya Visual Studio'nun XML düzenleyicisinde indirilen tüm snippet dosyalarını açın ve yüklemeden önce dikkatlice inceleyin. Aşağıdaki sorunları arayın:

  - Snippet kodu çalıştırdığınızda sisteminize zarar verebilir. Çalıştırmadan önce kaynak kodu dikkatle okuyun.

  - Parçacık dosyasının Yardım URL bloğu, kötü amaçlı bir komut dosyası dosyasını çalıştıran veya rahatsız edici bir web sitesi görüntüleyen URL'ler içerebilir.

  - Parçacık, projenize sessizce eklenen referanslar içerebilir ve sisteminizin herhangi bir yerinden yüklenebilir. Bu başvurular, parçacığı indirdiğiniz yerden bilgisayarınıza indirilmiş olabilir. Parçacık daha sonra kötü amaçlı kodu çalıştıran başvuruda bir yönteme çağrı yapabilir. Böyle bir saldırıya karşı kendinizi korumak için, parçacık dosyasının İçeriak ve Referanslar bloklarını gözden geçirin.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic IntelliSense kod parçacıkları](/dotnet/visual-basic/developing-apps/using-ide/intellisense-code-snippets)
- [Uygulamaları güvence altına alma](../ide/securing-applications.md)
- [Kod parçacıkları](../ide/code-snippets.md)
