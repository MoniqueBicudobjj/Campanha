let usuariosValidos = [
    { username: "admin@gmail.com", password: "123456" },
    { username: "usuario@gmail.com", password: "senha123" },
    { username: "angelina.becker@gmail.com", password: "123456789" }
];

const loginForm = document.getElementById('loginForm');
const registerForm = document.getElementById('registerForm');

document.getElementById('goToRegister').addEventListener('click', (e) => {
    e.preventDefault();
    loginForm.style.display = 'none';
    registerForm.style.display = 'block';
});

document.getElementById('goToLogin').addEventListener('click', (e) => {
    e.preventDefault();
    registerForm.style.display = 'none';
    loginForm.style.display = 'block';
});

function showTemporaryMessage(element, text, color) {
    element.textContent = text;
    element.style.color = color;
    setTimeout(() => element.textContent = '', 4000);
}

loginForm.addEventListener('submit', function (e) {
    e.preventDefault();
    const email = document.getElementById('email').value.trim();
    const senha = document.getElementById('senha').value;
    const messageDiv = document.getElementById('message');

    const encontrado = usuariosValidos.find(user => 
        user.username.toLowerCase() === email.toLowerCase() && user.password === senha
    );

    if (encontrado) {
        showTemporaryMessage(messageDiv, "✅ Login realizado com sucesso!", "green");
        setTimeout(() => window.location.href = "paginainicial.html", 1000);
    } else {
        showTemporaryMessage(messageDiv, "❌ Usuário ou senha incorretos.", "red");
    }
});

registerForm.addEventListener('submit', function (e) {
    e.preventDefault();

    const email = document.getElementById('regEmail').value.trim();
    const senha = document.getElementById('regSenha').value;
    const confirm = document.getElementById('regConfirmSenha').value;
    const regMessage = document.getElementById('registerMessage');

    if (senha !== confirm) {
        showTemporaryMessage(regMessage, "❌ As senhas não coincidem.", "red");
        return;
    }
    if (senha.length < 4) {
        showTemporaryMessage(regMessage, "❌ A senha deve ter pelo menos 4 caracteres.", "red");
        return;
    }

    if (usuariosValidos.some(user => user.username.toLowerCase() === email.toLowerCase())) {
        showTemporaryMessage(regMessage, "❌ Este e-mail já está cadastrado.", "red");
        return;
    }

    usuariosValidos.push({ username: email, password: senha });
    showTemporaryMessage(regMessage, "✅ Conta criada com sucesso!", "green");
    registerForm.reset();

    setTimeout(() => {
        registerForm.style.display = 'none';
        loginForm.style.display = 'block';
    }, 1500);
});
