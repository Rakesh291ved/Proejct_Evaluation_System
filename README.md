# Project Evaluation System

## Description

The Team Project Evaluation System is a comprehensive Django web application designed for managing and evaluating student projects. It provides role-based access for coordinators, students (teams), and panelists, enabling efficient project assessment through phase-wise tracking, file uploads, and detailed rubrics. The system streamlines the evaluation process with dashboards tailored to each user role.

## Features

- **Role-Based Dashboards**:
  - **Coordinator Dashboard**: Manage students, create teams, view evaluations, and track average marks across phases.
  - **Team Dashboard**: Upload project materials (PPT, phase files), view evaluations, and monitor progress.
  - **Panelist Dashboard**: Evaluate teams using detailed rubrics for each phase.
- **Phase-Wise Tracking**: Supports three phases with separate file uploads and evaluations.
- **File Uploads**: Upload PPT files, GitHub repos, and phase-specific documents.
- **Detailed Rubrics**: 15 criteria for evaluation, including abstract, relevance, communication skills, etc.
- **Average Marks Calculation**: Automatic calculation of total and average marks per phase and overall.
- **Responsive UI**: Built with Bootstrap for a clean, user-friendly interface.

## Technologies Used

- **Backend**: Django 5.1.3
- **Database**: SQLite (default; can be configured for others)
- **Frontend**: HTML, CSS, Bootstrap 5.1.3
- **Python Version**: Compatible with Python 3.x
- **Other**: FileField for uploads, Model-View-Template (MVT) architecture

## Installation

1. **Clone the Repository**:

   ```
   git clone <repository-url>
   cd Proejct_Evaluation_System
   ```

2. **Install Dependencies**:
   Ensure Python and pip are installed. Then run:

   ```
   pip install django
   ```

   (Add other dependencies if listed in requirements.txt; otherwise, Django is sufficient for basic setup.)

3. **Set Up Virtual Environment** (Recommended):
   ```
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   pip install django
   ```

## Setup

1. **Apply Migrations**:

   ```
   python manage.py makemigrations
   python manage.py migrate
   ```

2. **Create Superuser** (Optional, for admin access):

   ```
   python manage.py createsuperuser
   ```

3. **Run the Server**:
   ```
   python manage.py runserver
   ```
   Access the application at `http://127.0.0.1:8000/`.

## Usage

- **Home Page**: `http://127.0.0.1:8000/evaluation/home` - Overview with links to dashboards.
- **Coordinator Dashboard**: `http://127.0.0.1:8000/evaluation/coordinator` - Add students, create teams, view evaluations.
- **Team Dashboard**: `http://127.0.0.1:8000/evaluation/team/<team_id>/` (e.g., `http://127.0.0.1:8000/evaluation/team/17/`) - Upload files, view marks.
- **Panelist Dashboard**: `http://127.0.0.1:8000/evaluation/panelist` - Select team and phase, submit evaluations.

### Workflow

1. Coordinator adds students and creates teams.
2. Teams upload phase-specific files and PPT.
3. Panelists evaluate teams using the rubric form.
4. All roles can view marks and averages on their dashboards.

## Database Models

- **Student**: Stores student names.
- **Team**: Includes name, guide, GitHub repo, PPT file, phase files, students (ManyToMany), average marks.
- **Evaluation**: Linked to Team; includes panelist name, phase, and 15 rubric fields (e.g., abstract_synopsis, communication_skills); calculates total and average marks.

## Contributing

1. Fork the repository.
2. Create a feature branch: `git checkout -b feature-name`.
3. Commit changes: `git commit -m "Add feature"`.
4. Push to branch: `git push origin feature-name`.
5. Submit a pull request.

## License

This project is licensed under the MIT License. See LICENSE file for details.

## Notes

- Ensure uploaded files are in supported formats (e.g., PPT, DOCX, PDF).
- For production, update settings.py (e.g., DEBUG=False, secure SECRET_KEY).
- Database is SQLite by default; configure for PostgreSQL/MySQL if needed.
