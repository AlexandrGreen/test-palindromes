# Тестовое задание "Палиндром"
Дан массив, который может содержать любые типы переменных.\
Необходимо вывести на экран список из элементов массива, которые являются палиндромами.\

_Палиндром - Число, буквосочетание, слово или текст, одинаково читающееся в обоих направлениях.\
Например, число 101; слова «топот» в русском языке и saippuakivikauppias - самое длинное слово-палиндром в мире; текст «а роза упала на лапу Азора» и прочие являются палиндромами. Дата 22 февраля 2022 года тоже является палиндромом._
```javascript
function filterPalindromes(examplesArray = []) {
	if (!Array.isArray(examplesArray)) {
		return [];
	}
	return examplesArray.filter(example => {
		if (
			['string', 'number'].includes(typeof example)
			&& example // Исключить NaN, ...
		) {
			let prepared = ('' + example)
				.toLowerCase()
				.replace(/[^а-яa-z0-9]+/g, '')
				.split('');
			let left = prepared
				.slice(0, Math.floor(prepared.length / 2))
				.join('');
			let right = prepared
				.slice(-Math.floor(prepared.length / 2))
				.reverse()
				.join('');
			return left === right;
		} else {
			return false;
		}
	})
}
```
```javascript
const examples = [
	'Муза, ранясь шилом опыта, ты помолишься на разума',
	'шалаш',
	false,
	12342321,
	'потоп',
	8282882892,
	[],
	[1, 2, 2, 2, 3],
	true,
	123433334321,
	'манекенам',
	'водоворот',
	'Он рёва наверно',
];
console.log('filterPalindromes(examples)', filterPalindromes(examples)); // ['шалаш', 'потоп', 123433334321, 'манекенам']
```