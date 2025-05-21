// Подключаем модуль для работы с файлами
const fs = require('fs');

// Проверяем, переданы ли оба аргумента: количество этажей и путь к файлу
const args = process.argv.slice(2);

// Если аргументов меньше двух — выводим ошибку и завершаем программу
if (args.length < 2) {
    console.log("Ошибка: Не указано количество этажей или путь к файлу.");
    console.log("Пример использования: node tree.js 4 tree.txt");
    process.exit(1);
}

// Преобразуем введённое значение в число
let floors = parseInt(args[0]);

// Путь к выходному файлу
let outputPath = args[1];

// Проверяем, что введено корректное положительное число
if (isNaN(floors) || floors <= 0) {
    console.log("Ошибка: Введите положительное число для количества этажей.");
    console.log("Пример: node tree.js 4 tree.txt");
    process.exit(1);
}

// Вычисляем ширину самой длинной строки для центрирования
let width = 6 + 4 * (floors - 1);

// Массив для хранения всех строк
let lines = [];

// Верхушка: "W"
lines.push(" ".repeat((width - 1) / 2) + "W" + " ".repeat((width - 1) / 2));

// Верхушка: "*"
lines.push(" ".repeat((width - 1) / 2) + "*" + " ".repeat((width - 1) / 2));

// Сами этажи
for (let i = 0; i < floors; i++) {
    let stars = 5 + i * 4;

    // Определяем, где будет символ @: в начале или в конце
    let floorLine;
    if (i % 2 === 0) {
        // Чётный этаж: @ в начале, звёздочки без @ в конце
        floorLine = "@" + "*".repeat(stars);
    } else {
        // Нечётный этаж: звёздочки без @ в начале, @ в конце
        floorLine = "*".repeat(stars) + "@";
    }

    // Центрируем строку
    let spaces = " ".repeat((width - floorLine.length) / 2);
    lines.push(spaces + floorLine + spaces);
}

// Ствол дерева где две строки "TTTTT"
for (let i = 0; i < 2; i++) {
    let trunk = " ".repeat((width - 5) / 2) + "TTTTT" + " ".repeat((width - 5) / 2);
    lines.push(trunk);
}

// Объединяем все строки в одну с переносами
let result = lines.join("\n");

// Записываем результат в указанный файл
try {
    fs.writeFileSync(outputPath, result);
    console.log(`Ёлка успешно записана в файл: ${outputPath}`);
} catch (err) {
    console.error(`Ошибка при записи в файл: ${err.message}`);
    process.exit(1);
}
