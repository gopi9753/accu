import React, { useState } from 'react';
import { Check } from "lucide-react";

interface Task {
  id: number;
  name: string;
  completed: boolean;
}

const tasks: Task[] = [
  { id: 1, name: 'Develop a Dockerfile for the Wisecow application.', completed: false },
  { id: 2, name: 'Create Kubernetes manifest files for deployment.', completed: false },
  { id: 3, name: 'Generate TLS certificates.', completed: false },
  { id: 4, name: 'Implement a GitHub Actions workflow for CI/CD.', completed: false },
];

const App = () => {
  const [taskList, setTaskList] = useState(tasks);

  const handleToggleTask = (id: number) => {
    setTaskList(taskList.map((task) => task.id === id ? { ...task, completed: !task.completed } : task));
  };

  return (
    <div className="max-w-3xl mx-auto p-4">
      <h1 className="text-3xl font-bold mb-4">Wisecow Implementation Plan</h1>
      <ul className="list-none">
        {taskList.map((task) => (
          <li key={task.id} className="flex items-center mb-2">
            <button onClick={() => handleToggleTask(task.id)} className="mr-2">
              {task.completed ? <Check className="text-green-500" /> : <div className="w-4 h-4 border-2 border-gray-300 rounded" />}
            </button>
            <span className={task.completed ? 'text-gray-500 line-through' : 'text-gray-700'}>{task.name}</span>
          </li>
        ))}
      </ul>
    </div>
  );
};

export default App;
