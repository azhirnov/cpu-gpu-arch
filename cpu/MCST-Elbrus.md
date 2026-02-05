
## References

1. [E2Kh](https://t.me/e2k_fans/1591), [[video](https://t.me/e2k_fans/1592)], [[backup](../pdf/Elbrus-E2Kh.pdf)]
2. [Features of the topological planning of cores (2017)](https://t.me/e2k_fans/1586), [[backup](../pdf/Elbrus-osobennosti_tehnologicheskogo_planirovaniya_yader_vysokoskorostnyh_protsessorov_semeystva_elbrus.pdf)]
	* [new](https://www.nanoindustry.su/files/article_pdf/6/article_6754_973.pdf), [[backup](../pdf/Elbrus-article_6754_973.pdf)]
3. [Secure computing technology](https://mcst.ru/sites/default/files/u11/Elbrus_secure_computing_2023-09-26_ru.pdf), [[backup](../pdf/Elbrus-secure_computing_2023-09-26_ru.pdf)]
4. [ISA Review (2025)](http://www.iakovlev.org/index.html?p=8912&m=1&l1=7), [[backup](../pdf/Elbrus-e2k_ISA_review.pdf)]


**Development Tools**
* [Dev News](https://dev.mcst.ru)
* [Cross compiler](https://dev.mcst.ru/download/) and [how to setup](https://habr.com/ru/articles/898040/)
* [QEMU With E2K User Support](https://github.com/OpenE2K/qemu-e2k)
* [Clang for e2k](https://git.openelbrus.ru/unipro/llvm-e2k)

**Porting**
* [Porting on Elbrus](https://www.altlinux.org/%D0%AD%D0%BB%D1%8C%D0%B1%D1%80%D1%83%D1%81/%D0%BF%D0%BE%D1%80%D1%82%D0%B8%D1%80%D0%BE%D0%B2%D0%B0%D0%BD%D0%B8%D0%B5)
* [How-to compile games on e2k](https://www.altlinux.org/How-to_compile_games_on_e2k)
* [GPU compatibility](https://www.altlinux.org/%D0%AD%D0%BB%D1%8C%D0%B1%D1%80%D1%83%D1%81/hcl/gpu)


## Notes

* Архитектура «Эльбрус» вводит режимы спекулятивности по управлению и спекулятивности по данным. [4]
	- Для спекулятивной по управлению операции факт возникшей исключительной операции (чтение по недопустимому адресу, деление на 0 и т.п.) сохраняется в значении результата операции. Однако сама исключительная ситуация откладывается до выяснения того, должна ли была быть выполнена эта операция на самом деле.
	- Спекулятивность по данным доступна посредством пары операций:
		* верхняя операция читает данные;
		* нижняя проверяет, была ли спекулятивно прочтенная ячейка памяти частично перезаписана с момента первой операции, и заново выполняет чтение в том случае, если это произошло.

