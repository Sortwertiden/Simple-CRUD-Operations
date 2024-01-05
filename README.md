# Simple-CRUD-Operations
Simple CRUD Operations with MongoDB and Node.js
const mongoose = require('mongoose');
mongoose.connect('mongodb://localhost/test', { useNewUrlParser: true });

const Note = mongoose.model('Note', { text: String });

// Create
const newNote = new Note({ text: 'Hello, MongoDB!' });
newNote.save().then(() => console.log('Note saved'));

// Read
Note.find({ text: 'Hello, MongoDB!' }, (err, notes) => {
    if (err) throw err;
    console.log(notes);
});

// Update
Note.updateOne({ text: 'Hello, MongoDB!' }, { text: 'Updated text' }, (err) => {
    if (err) throw err;
    console.log('Note updated');
});

// Delete
Note.deleteOne({ text: 'Updated text' }, (err) => {
    if (err) throw err;
    console.log('Note deleted');
});
