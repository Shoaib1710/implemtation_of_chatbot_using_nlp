This error occurs because signal.signal(signal.SIGINT, signal.SIG_IGN) can only be called from the main thread, but in your case, it's being executed in a different thread. This is common when using Jupyter notebooks or IPython in certain environments (e.g., running in an IDE like PyCharm, or within some multiprocessing setups).

Possible Fixes:
1. Run the Code in the Main Thread
If you're running a script, ensure it's executed directly in the main thread and not within a multiprocessing context.
2. Use ipykernel Workaround
Try launching Jupyter Notebook with the --no-browser flag:

sh
Copy
Edit
jupyter notebook --no-browser
Or, if you're using Jupyter Lab:

sh
Copy
Edit
jupyter lab --no-browser
3. Downgrade ipykernel (if issue persists)
If this started happening after an update, try rolling back ipykernel:

sh
Copy
Edit
pip install ipykernel==6.25.0
4. Check Python Version
Some users report this issue more frequently in Python 3.12. If possible, try using Python 3.10 or 3.11.

Let me know if you need further assistance! 🚀