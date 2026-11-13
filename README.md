from pathlib import Path

def generate_readme():
    print("=== GitHub Profile README Generator ===")

    name = input("Your name: ").stri()
    bio = input("Short bio: ").strip()
    skills = input("Your skills (Python, HTML, etc.): ").strip()
    projects = input("Your favorite projects: ").strip()
    github = input("GitHub username: ").strip()

    if not name or not github:
        print("Name and GitHub username are required.")
        return

    skill_list = [
        skill.strip()
        for skill in skills.split(",")
        if skill.strip()
    ]

    project_list = [
        project.strip()
        for project in projects.split(",")
        if project.strip()
    ]

    readme = f"""# Hi, I'm {name}!

## About Me
{bio}

## Skills
{', '.join(skill_list) if skill_list else 'Learning new technologies'}

## Projects
"""

    if project_list:
        for project in project_list:
            readme += f"- {project}\n"
    else:
        readme += "- Coming soon!\n"

    readme += f"""
## GitHub Profile
[Visit my GitHub](https://github.com/{github})

---
Thanks for visiting my profile!
"""

    Path("README.md").write_text(
        readme, encoding="utf-8"
    )

    print("\nREADME.md created successfully!")

if __name__ == "__main__":
    generate_readme()
