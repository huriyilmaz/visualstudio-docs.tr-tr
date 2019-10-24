---
title: Kaynak denetim bilgilerini. proj ve. sln dosyalarından kaldır
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, .sln and .proj files
ms.assetid: 7b06883f-35de-41e2-9a9e-d3edba236f17
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 68e50932a83e3db6d405119d3721d021144cbaeb
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724272"
---
# <a name="removal-of-source-control-information-from-proj-and-sln-files"></a>.Proj ve .Sln Dosyalarından Kaynak Denetimi Bilgilerinin Kaldırılması
Kaynak denetimi eklentisi API 'sinin sürüm 1,2 ' de, SCC bilgileri bir MSSCCPRJ depolanır. SCC dosyası. MSSCCPRJ avantajı. SCC dosyası. proj ve. sln dosyalarında olduğu gibi, SCC bilgisinin kaynak denetimli olmaması olabilir.

## <a name="version-12-changes"></a>Sürüm 1,2 değişiklikleri
 Kaynak denetimi eklentisi API sürüm 1,1 ' i temel alan kaynak denetimi eklentilerinde, kaynak denetimi ile ilgili bilgiler proje (. proj) ve çözüm (. sln) dosyalarında depolanır. Kaynak denetim bilgisinin veritabanı konumu AuxPath tarafından belirtilir ve veritabanı içindeki belirli konum ProjName tarafından belirtilir. Bu davranış, bu işlemlerden herhangi biri sonrasında ProjName genellikle geçersiz olacağından, dal, çatal veya kopyalama işlemlerinden sonra sorunlara yol açabilir.

 Kaynak denetimi eklentisi API sürümü 1,1 ' de, IDE, bir eklentinin MSSCCPRJ tarafından desteklenip desteklenmediğini algılamak için ~ SAK dosyalarını kullandı. Kaynak denetim bilgilerini depolamanın SCC yöntemi. Kaynak denetimi eklentisi API sürümü 1,2, MSSCCPRJ desteğini algılamaya yönelik yeni bir özellik sunar. Bir ~ SAK dosyası kullanmadan SCC dosyası. Daha fazla bilgi için bkz. yok [~ sak Files](../../extensibility/internals/elimination-of-tilde-sak-files.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentisi API Sürümü 1.2’deki Yenilikler](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)