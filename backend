import express from "express";
import path from "path";
import cors from "cors";

const app = express();
app.use(cors());
app.use(express.json());

// Datos de ejemplo
let productos = [
  { id: 1, name: "Dona glaseada", price: 1200},
  { id: 2, name: "Churros", price: 900 },
  { id: 3, name: "Torta frita", price: 700 },
  { id: 4, name: "Bola de fraile", price: 1000 },
];
let pedidos = [];

// APIs
app.get("/api/productos", (req, res) => res.json(productos));
app.get("/api/pedidos", (req, res) => res.json(pedidos));
app.post("/api/pedidos", (req, res) => {
  const nuevoPedido = { ...req.body, status: "En preparación", timestamp: new Date().toLocaleString() };
  pedidos.unshift(nuevoPedido);
  res.json(nuevoPedido);
});

// Servir frontend build
app.use(express.static(path.join(__dirname, '../frontend/build')));
app.get("*", (req, res) => {
  res.sendFile(path.join(__dirname, '../frontend/build', 'index.html'));
});

const PORT = process.env.PORT || 4000;
app.listen(PORT, () => console.log(Servidor corriendo en http://localhost:${PORT}));
